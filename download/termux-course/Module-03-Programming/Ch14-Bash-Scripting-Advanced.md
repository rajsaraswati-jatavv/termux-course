# Chapter 14: Advanced Bash Scripting

> **Module:** 3 - Programming  
> **Chapter:** 14 of 61  
> **Duration:** 25-30 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate-Advanced

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Advanced bash scripting techniques |
| Code Examples | 30+ practical script examples |
| Commands Reference | Advanced commands and patterns |
| Practice Exercises | 5 complex scripting challenges |
| Troubleshooting | Debugging advanced scripts |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 14
Title: Advanced Bash Scripting | Next Level Scripting | T3rmuxk1ng
Duration: 25-30 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Previous chapter mein humne Bash scripting basics seekha tha - variables,
loops, functions, aur arrays. Aaj hum next level pe jaayenge!

Advanced Bash Scripting chapter mein hum cover karenge:
- Error handling aur trapping
- Signal handling
- Regular expressions
- Process management
- Here documents aur here strings
- Process substitution
- Advanced text processing
- CLI tools building
- Security best practices

Ye chapter aapko professional-level bash developer banayega!

To chaliye shuru karte hain!

---

[SECTION 1: ERROR HANDLING - 1:00 to 5:00]
─────────────────────────────────────────────────────────────────────────────

Production-level scripts mein error handling sabse important hai.

### set Options

Bash mein `set` command se script behavior control karte hain:

    #!/bin/bash
    set -e  # Exit immediately if a command exits with non-zero status
    set -u  # Treat unset variables as an error
    set -o pipefail  # Return value of a pipeline is the status of the last command to exit with non-zero status
    set -x  # Print commands and their arguments as they are executed

    # Combined strict mode:
    set -euo pipefail

Example:

    #!/bin/bash
    set -euo pipefail

    echo "Creating directory..."
    mkdir /tmp/myproject

    echo "Changing to directory..."
    cd /tmp/myproject

    echo "Creating file..."
    touch important.txt

    echo "All operations completed!"

Agar koi bhi command fail hoti hai, script immediately exit ho jaayega.

### trap Command

trap se aap signals aur errors handle kar sakte ho:

    #!/bin/bash

    cleanup() {
        echo "Cleaning up temporary files..."
        rm -f /tmp/mytemp_*
        echo "Cleanup completed!"
    }

    # Trap EXIT signal - runs on script exit (success or failure)
    trap cleanup EXIT

    # Trap interrupts (Ctrl+C)
    trap 'echo "Interrupted!"; exit 130' INT

    # Trap termination signal
    trap 'echo "Terminated!"; exit 143' TERM

    # Trap errors
    trap 'echo "Error on line $LINENO"' ERR

    # Main script logic
    echo "Script starting..."
    # Your code here
    echo "Script completed!"

### Error Handling Best Practices

    #!/bin/bash
    set -euo pipefail

    # Logging function
    log() {
        echo "[$(date '+%Y-%m-%d %H:%M:%S')] $*" >&2
    }

    error() {
        log "ERROR: $*"
        exit 1
    }

    # Check command success
    check_command() {
        if ! command -v "$1" &> /dev/null; then
            error "$1 is not installed"
        fi
    }

    # Validate arguments
    if [[ $# -lt 1 ]]; then
        echo "Usage: $0 <argument>"
        exit 1
    fi

    # Safe file operations
    safe_write() {
        local file="$1"
        local content="$2"
        
        # Check if file exists and is writable
        if [[ -f "$file" ]] && [[ ! -w "$file" ]]; then
            error "Cannot write to $file"
        fi
        
        echo "$content" > "$file" || error "Failed to write to $file"
    }

---

[SECTION 2: SIGNAL HANDLING - 5:00 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Signals OS-level notifications hain jo scripts ko handle karni padti hain.

### Common Signals

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON UNIX SIGNALS                                   │
├─────────┬──────────────────────┬────────────────────────────────────────┤
│ Signal  │ Description          │ Default Action                        │
├─────────┼──────────────────────┼────────────────────────────────────────┤
│ SIGINT  │ Interrupt (Ctrl+C)   │ Terminate                             │
│ SIGTERM │ Termination request  │ Terminate                             │
│ SIGKILL │ Kill (uncatchable)   │ Terminate                             │
│ SIGHUP  │ Hangup               │ Terminate                             │
│ SIGSTOP │ Stop (uncatchable)   │ Stop                                  │
│ SIGCONT │ Continue             │ Continue                              │
│ SIGUSR1 │ User-defined 1       │ Terminate                             │
│ SIGUSR2 │ User-defined 2       │ Terminate                             │
└─────────┴──────────────────────┴────────────────────────────────────────┘

### Signal Handling Example

    #!/bin/bash

    # Global variables
    RUNNING=true
    COUNTER=0

    # Signal handlers
    handle_int() {
        echo ""
        echo "Received SIGINT (Ctrl+C)"
        echo "Shutting down gracefully..."
        RUNNING=false
    }

    handle_term() {
        echo "Received SIGTERM"
        echo "Performing cleanup..."
        cleanup
        exit 0
    }

    handle_hup() {
        echo "Received SIGHUP - Reloading configuration..."
        # Reload config here
    }

    cleanup() {
        echo "Cleaning up resources..."
        rm -f /tmp/script_lock_$$
        echo "Cleanup complete!"
    }

    # Set up traps
    trap handle_int INT
    trap handle_term TERM
    trap handle_hup HUP
    trap cleanup EXIT

    # Main loop
    echo "Script PID: $$"
    echo "Press Ctrl+C to stop..."

    while $RUNNING; do
        ((COUNTER++))
        echo "Running... Count: $COUNTER"
        sleep 1
    done

    echo "Script ended gracefully."

### Process Control

    #!/bin/bash

    # Run background process
    long_running_task() {
        for i in {1..100}; do
            echo "Processing: $i"
            sleep 1
        done
    }

    # Start background process
    long_running_task &
    BG_PID=$!

    echo "Background process started with PID: $BG_PID"

    # Monitor process
    while kill -0 $BG_PID 2>/dev/null; do
        echo "Process $BG_PID still running..."
        sleep 5
    done

    echo "Process $BG_PID has completed"

    # Wait for process with timeout
    wait_with_timeout() {
        local pid=$1
        local timeout=$2
        
        for ((i=0; i<timeout; i++)); do
            if ! kill -0 $pid 2>/dev/null; then
                return 0  # Process finished
            fi
            sleep 1
        done
        
        # Timeout reached, kill process
        kill -9 $pid 2>/dev/null
        return 1  # Timed out
    }

---

[SECTION 3: REGULAR EXPRESSIONS - 9:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Bash supports regular expressions through `=~` operator and external tools.

### Bash Regex

    #!/bin/bash

    # Basic regex matching with [[ ]]
    validate_email() {
        local email="$1"
        local regex="^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"
        
        if [[ $email =~ $regex ]]; then
            echo "Valid email: $email"
            return 0
        else
            echo "Invalid email: $email"
            return 1
        fi
    }

    # Extract matched groups
    parse_url() {
        local url="$1"
        local regex="^(https?)://([^/]+)(/.*)?$"
        
        if [[ $url =~ $regex ]]; then
            echo "Protocol: ${BASH_REMATCH[1]}"
            echo "Domain: ${BASH_REMATCH[2]}"
            echo "Path: ${BASH_REMATCH[3]:-/}"
        fi
    }

    # Test
    parse_url "https://example.com/path/to/page"

### Common Regex Patterns

    #!/bin/bash

    # IP Address validation
    is_valid_ip() {
        local ip="$1"
        local regex="^([0-9]{1,3}\.){3}[0-9]{1,3}$"
        
        [[ $ip =~ $regex ]] || return 1
        
        # Validate each octet
        IFS='.' read -ra octets <<< "$ip"
        for octet in "${octets[@]}"; do
            (( octet > 255 )) && return 1
        done
        return 0
    }

    # Phone number validation (Indian format)
    is_valid_phone() {
        local phone="$1"
        local regex="^[6-9][0-9]{9}$"
        [[ $phone =~ $regex ]]
    }

    # Strong password check
    check_password_strength() {
        local pass="$1"
        
        [[ ${#pass} -ge 8 ]] || { echo "Too short"; return 1; }
        [[ $pass =~ [A-Z] ]] || { echo "No uppercase"; return 1; }
        [[ $pass =~ [a-z] ]] || { echo "No lowercase"; return 1; }
        [[ $pass =~ [0-9] ]] || { echo "No number"; return 1; }
        [[ $pass =~ [!@#$%^&*] ]] || { echo "No special char"; return 1; }
        
        echo "Strong password!"
        return 0
    }

### grep with Regex

    # Extended regex with grep
    grep -E "pattern" file.txt

    # Perl-compatible regex
    grep -P "pattern" file.txt

    # Examples:
    grep -E "^[A-Z]" file.txt           # Lines starting with uppercase
    grep -E "[0-9]{4}-[0-9]{2}-[0-9]{2}" file.txt  # Date patterns
    grep -E "\bword\b" file.txt         # Whole word match
    grep -Ei "error|warning" file.txt   # Case insensitive OR

### sed with Regex

    # Replace patterns
    sed 's/old/new/g' file.txt

    # Delete lines matching pattern
    sed '/pattern/d' file.txt

    # Extract text between markers
    sed -n '/START/,/END/p' file.txt

    # Complex substitution
    sed -E 's/([0-9]+)/[\1]/g' file.txt  # Wrap numbers in brackets

### awk with Regex

    # Field extraction
    awk -F',' '{print $1, $3}' file.csv

    # Pattern matching
    awk '/error/ {print $0}' log.txt

    # Complex processing
    awk '$3 > 100 {sum += $3} END {print sum}' data.txt

---

[SECTION 4: PROCESS SUBSTITUTION - 14:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Process substitution command output ko temporary file ki tarah treat karta hai.

### Input Process Substitution <()

    # Compare outputs of two commands
    diff <(ls dir1) <(ls dir2)

    # Sort and compare
    diff <(sort file1.txt) <(sort file2.txt)

    # Use with while loop
    while read line; do
        echo "Processing: $line"
    done < <(grep "error" logfile.txt)

    # Multiple inputs
    cat <(echo "Header") <(cat data.txt) <(echo "Footer")

### Output Process Substitution >()

    # Tee to multiple processes
    tee >(process1) >(process2) > output.txt

    # Log and process simultaneously
    command | tee >(grep "error" > errors.txt) >(grep "warning" > warnings.txt)

    # Parallel processing
    process_data() {
        while read line; do
            echo "Processed: $line"
        done
    }
    export -f process_data

    cat data.txt > >(process_data) > >(process_data)

### Named Pipes (FIFOs)

    #!/bin/bash

    # Create named pipe
    PIPE=/tmp/my_pipe_$$
    mkfifo "$PIPE"

    # Writer process
    (
        for i in {1..10}; do
            echo "Message $i" > "$PIPE"
            sleep 1
        done
        echo "DONE" > "$PIPE"
    ) &

    # Reader process
    while read line < "$PIPE"; do
        [[ "$line" == "DONE" ]] && break
        echo "Received: $line"
    done

    # Cleanup
    rm "$PIPE"

---

[SECTION 5: HERE DOCUMENTS & HERE STRINGS - 17:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Here documents multi-line text input provide karte hain.

### Here Documents

    #!/bin/bash

    # Basic here document
    cat << EOF
    This is a multi-line
    text block that can
    contain variables: $HOME
    and commands: $(date)
    EOF

    # Quoted delimiter (no variable expansion)
    cat << 'EOF'
    Variables won't expand: $HOME
    Commands won't run: $(date)
    EOF

    # Indented here document (strip leading tabs)
    cat <<- EOF
        This is indented
        but tabs are removed
    EOF

    # Here document to file
    cat > config.txt << EOF
    # Configuration file
    host=localhost
    port=8080
    debug=false
    EOF

    # Here document to function
    configure() {
        cat << EOF
    Setting up $1...
    Configuration complete!
    EOF
    }

    configure "myproject"

### Here Strings

    #!/bin/bash

    # Single line input
    grep "pattern" <<< "search in this string"

    # With read command
    read -r a b c <<< "one two three"
    echo "a=$a, b=$b, c=$c"

    # With awk
    awk '{print $2}' <<< "first second third"

    # Variable as input
    data="line1 line2 line3"
    while read word; do
        echo "Word: $word"
    done <<< "$data"

### Practical Applications

    #!/bin/bash

    # Generate HTML
    generate_html() {
        local title="$1"
        local content="$2"
        
        cat << EOF
    <!DOCTYPE html>
    <html>
    <head>
        <title>$title</title>
    </head>
    <body>
        $content
    </body>
    </html>
    EOF
    }

    # Create SSH config
    create_ssh_config() {
        cat > ~/.ssh/config << 'EOF'
    Host github.com
        User git
        IdentityFile ~/.ssh/github_key
        IdentitiesOnly yes

    Host server
        HostName example.com
        User admin
        Port 2222
    EOF
    }

    # Parse JSON-like data
    parse_data() {
        while IFS='=' read -r key value; do
            printf "%-15s: %s\n" "$key" "$value"
        done <<< "
    name=Alice
    age=30
    city=Mumbai
    "
    }

---

[SECTION 6: ADVANCED TEXT PROCESSING - 20:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

### Advanced sed Patterns

    #!/bin/bash

    # In-place editing
    sed -i 's/old/new/g' file.txt

    # Backup and edit
    sed -i.bak 's/old/new/g' file.txt

    # Multiple commands
    sed -e 's/foo/bar/g' -e 's/baz/qux/g' file.txt

    # Print specific lines
    sed -n '10,20p' file.txt    # Lines 10-20
    sed -n '5p' file.txt        # Line 5 only

    # Delete lines
    sed '5d' file.txt           # Delete line 5
    sed '/pattern/d' file.txt   # Delete matching lines
    sed '5,10d' file.txt        # Delete lines 5-10

    # Insert and append
    sed '5i\New line before 5' file.txt
    sed '5a\New line after 5' file.txt

    # Change case
    sed 's/.*/\U&/' file.txt    # Uppercase
    sed 's/.*/\L&/' file.txt    # Lowercase

### Advanced awk Patterns

    #!/bin/bash

    # Field manipulation
    awk -F':' '{print $1, $3}' /etc/passwd

    # Custom field separator
    awk -F'[,:]' '{print $1, $2}' file.txt

    # NR (Number of Records) and NF (Number of Fields)
    awk '{print NR": "$0}' file.txt
    awk '{print NF" fields"}' file.txt

    # Conditional processing
    awk '$3 > 50 {print $1, $3}' data.txt

    # Calculations
    awk '{sum += $1} END {print "Sum:", sum}' numbers.txt
    awk '{sum += $1} END {print "Average:", sum/NR}' numbers.txt

    # Arrays in awk
    awk '{count[$1]++} END {for (word in count) print word, count[word]}' file.txt

    # Custom functions
    awk '
    function reverse(s) {
        n = split(s, chars, "")
        result = ""
        for (i = n; i >= 1; i--)
            result = result chars[i]
        return result
    }
    {print reverse($0)}
    ' file.txt

### Text Processing Functions

    #!/bin/bash

    # Count occurrences
    count_occurrences() {
        local pattern="$1"
        local file="$2"
        grep -o "$pattern" "$file" | wc -l
    }

    # Extract between patterns
    extract_between() {
        local start="$1"
        local end="$2"
        local file="$3"
        sed -n "/$start/,/$end/p" "$file" | sed '1d;$d'
    }

    # Remove duplicates while preserving order
    remove_duplicates() {
        awk '!seen[$0]++' "$1"
    }

    # Sort by specific column
    sort_by_column() {
        local col="$1"
        local file="$2"
        sort -t',' -k"$col","$col" "$file"
    }

    # CSV processing
    process_csv() {
        local file="$1"
        awk -F',' '
        NR == 1 {print; next}  # Print header
        {
            # Process each row
            gsub(/"/, "", $0)  # Remove quotes
            print $1, $2, $3
        }
        ' "$file"
    }

---

[SECTION 7: BUILDING CLI TOOLS - 24:00 to 27:00]
─────────────────────────────────────────────────────────────────────────────

### Argument Parsing with getopts

    #!/bin/bash

    # Usage function
    usage() {
        cat << EOF
    Usage: $0 [OPTIONS] FILE

    Options:
        -h          Show this help message
        -v          Verbose output
        -o FILE     Output file
        -n NUMBER   Number of iterations
        -f          Force operation

    Examples:
        $0 -v input.txt
        $0 -o output.txt -n 10 input.txt
    EOF
    }

    # Default values
    verbose=false
    output=""
    iterations=1
    force=false

    # Parse options
    while getopts ":hvo:n:f" opt; do
        case $opt in
            h) usage; exit 0 ;;
            v) verbose=true ;;
            o) output="$OPTARG" ;;
            n) iterations="$OPTARG" ;;
            f) force=true ;;
            \?) echo "Invalid option: -$OPTARG" >&2; usage; exit 1 ;;
            :) echo "Option -$OPTARG requires an argument." >&2; usage; exit 1 ;;
        esac
    done

    # Shift past options
    shift $((OPTIND-1))

    # Check for required argument
    if [[ $# -lt 1 ]]; then
        echo "Error: FILE argument required" >&2
        usage
        exit 1
    fi

    input_file="$1"

    # Main logic
    $verbose && echo "Processing $input_file..."
    $verbose && echo "Iterations: $iterations"
    $verbose && echo "Force: $force"
    $verbose && echo "Output: ${output:-stdout}"

    # Your processing here
    echo "File: $input_file"

### Advanced Argument Parsing

    #!/bin/bash

    # Long options support
    parse_args() {
        while [[ $# -gt 0 ]]; do
            case "$1" in
                --help|-h)
                    show_help
                    exit 0
                    ;;
                --verbose|-v)
                    VERBOSE=true
                    shift
                    ;;
                --output=*|-o=*)
                    OUTPUT="${1#*=}"
                    shift
                    ;;
                --output|-o)
                    OUTPUT="$2"
                    shift 2
                    ;;
                --count=*|-c=*)
                    COUNT="${1#*=}"
                    shift
                    ;;
                --)
                    shift
                    break
                    ;;
                -*)
                    echo "Unknown option: $1" >&2
                    exit 1
                    ;;
                *)
                    POSITIONAL_ARGS+=("$1")
                    shift
                    ;;
            esac
        done

        # Restore positional arguments
        set -- "${POSITIONAL_ARGS[@]}"
    }

### Complete CLI Tool Template

    #!/usr/bin/env bash
    #
    # tool - A powerful CLI tool
    #
    # Usage: tool [OPTIONS] COMMAND [ARGS]
    #

    set -euo pipefail

    # Constants
    readonly VERSION="1.0.0"
    readonly SCRIPT_NAME="$(basename "$0")"

    # Colors
    readonly RED='\033[0;31m'
    readonly GREEN='\033[0;32m'
    readonly YELLOW='\033[0;33m'
    readonly BLUE='\033[0;34m'
    readonly NC='\033[0m' # No Color

    # Logging functions
    log() { echo -e "${BLUE}[INFO]${NC} $*"; }
    success() { echo -e "${GREEN}[SUCCESS]${NC} $*"; }
    warn() { echo -e "${YELLOW}[WARNING]${NC} $*" >&2; }
    error() { echo -e "${RED}[ERROR]${NC} $*" >&2; }
    die() { error "$*"; exit 1; }

    # Show help
    show_help() {
        cat << EOF
    ${SCRIPT_NAME} - A powerful CLI tool

    USAGE:
        ${SCRIPT_NAME} [OPTIONS] <COMMAND>

    COMMANDS:
        init        Initialize a new project
        build       Build the project
        test        Run tests
        deploy      Deploy the project
        clean       Clean temporary files

    OPTIONS:
        -h, --help      Show this help message
        -v, --version   Show version
        -V, --verbose   Enable verbose output
        -q, --quiet     Suppress output

    EXAMPLES:
        ${SCRIPT_NAME} init myproject
        ${SCRIPT_NAME} build --release
        ${SCRIPT_NAME} test -v

    VERSION:
        ${VERSION}
    EOF
    }

    # Commands
    cmd_init() {
        local project="${1:-}"
        [[ -z "$project" ]] && die "Project name required"
        
        log "Initializing project: $project"
        mkdir -p "$project"/{src,tests,docs}
        touch "$project"/README.md
        success "Project $project initialized!"
    }

    cmd_build() {
        log "Building project..."
        # Build logic here
        success "Build complete!"
    }

    cmd_test() {
        log "Running tests..."
        # Test logic here
        success "All tests passed!"
    }

    cmd_deploy() {
        log "Deploying..."
        # Deploy logic here
        success "Deployed successfully!"
    }

    cmd_clean() {
        log "Cleaning..."
        rm -rf /tmp/project_*
        success "Cleaned!"
    }

    # Main function
    main() {
        local verbose=false
        local quiet=false

        # Parse global options
        while [[ $# -gt 0 ]]; do
            case "$1" in
                -h|--help) show_help; exit 0 ;;
                -v|--version) echo "${SCRIPT_NAME} ${VERSION}"; exit 0 ;;
                -V|--verbose) verbose=true; shift ;;
                -q|--quiet) quiet=true; shift ;;
                --) shift; break ;;
                -*) error "Unknown option: $1"; show_help; exit 1 ;;
                *) break ;;
            esac
        done

        # Check for command
        [[ $# -lt 1 ]] && { error "Command required"; show_help; exit 1; }

        local command="$1"
        shift

        # Execute command
        case "$command" in
            init) cmd_init "$@" ;;
            build) cmd_build "$@" ;;
            test) cmd_test "$@" ;;
            deploy) cmd_deploy "$@" ;;
            clean) cmd_clean "$@" ;;
            *) error "Unknown command: $command"; show_help; exit 1 ;;
        esac
    }

    main "$@"

---

[SECTION 8: SECURITY BEST PRACTICES - 27:00 to 29:00]
─────────────────────────────────────────────────────────────────────────────

### Secure Scripting Guidelines

    #!/bin/bash

    # 1. Validate all input
    validate_input() {
        local input="$1"
        
        # Check length
        [[ ${#input} -gt 100 ]] && return 1
        
        # Check for dangerous characters
        [[ "$input" =~ [;\|\&\`\$\(\)] ]] && return 1
        
        return 0
    }

    # 2. Avoid eval
    # Bad:
    # eval "echo $user_input"

    # Good:
    echo "$user_input"

    # 3. Use quoted variables
    [[ "$var" == "value" ]]

    # 4. Use absolute paths for critical commands
    /bin/rm file.txt

    # 5. Set secure umask
    umask 077

    # 6. Check file permissions
    check_permissions() {
        local file="$1"
        local expected="$2"
        local actual
        
        actual=$(stat -c "%a" "$file")
        [[ "$actual" == "$expected" ]] || return 1
    }

    # 7. Use temporary files securely
    create_temp_file() {
        local prefix="$1"
        mktemp "${prefix}_XXXXXX" || exit 1
    }

    # 8. Clean up sensitive data
    cleanup_sensitive() {
        # Overwrite before delete
        shred -u sensitive_file.txt 2>/dev/null || rm -f sensitive_file.txt
    }

---

[SECTION 9: SUMMARY & NEXT PREVIEW - 29:00 to 30:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 14 complete! Let's summarize:

✅ Error handling with set options and trap
✅ Signal handling for graceful shutdown
✅ Regular expressions in Bash
✅ Process substitution for powerful pipelines
✅ Here documents and here strings
✅ Advanced text processing with sed/awk
✅ Building professional CLI tools
✅ Security best practices

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 14 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ set -euo pipefail       │ Strict mode for scripts                       │
│ trap 'cmd' SIGNAL       │ Handle signals                                │
│ [[ $str =~ regex ]]     │ Regex matching                                │
│ diff <(cmd1) <(cmd2)    │ Process substitution                          │
│ cat << EOF ... EOF      │ Here document                                 │
│ grep -E "pattern"       │ Extended regex                                │
│ sed -i 's/old/new/g'    │ In-place edit                                 │
│ awk '{print $1}'        │ Field extraction                              │
│ getopts                 │ Parse command options                         │
│ mktemp                  │ Create secure temp files                      │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 15 mein hum seekhenge:
- Git version control in Termux
- Repository management
- Branching and merging
- GitHub integration

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 15!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### Advanced Bash Patterns Reference

```bash
# 1. Strict Mode Template
#!/usr/bin/env bash
set -euo pipefail
IFS=$'\n\t'

# 2. Safe Script Template
#!/usr/bin/env bash
set -euo pipefail

# Constants
readonly SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
readonly SCRIPT_NAME="$(basename "${BASH_SOURCE[0]}")"

# Cleanup function
cleanup() {
    # Remove temporary files
    [[ -f "$TEMP_FILE" ]] && rm -f "$TEMP_FILE"
}
trap cleanup EXIT

# Main function
main() {
    # Script logic here
}

main "$@"
```

### Regular Expression Quick Reference

| Pattern | Meaning |
|---------|---------|
| `^` | Start of line |
| `$` | End of line |
| `.` | Any single character |
| `*` | Zero or more occurrences |
| `+` | One or more occurrences |
| `?` | Zero or one occurrence |
| `[abc]` | Any character in set |
| `[^abc]` | Any character NOT in set |
| `[a-z]` | Character range |
| `\b` | Word boundary |
| `\d` | Digit |
| `\w` | Word character |
| `\s` | Whitespace |
| `(...)` | Capture group |
| `\|` | Alternation (OR) |

---

## ⚡ QUICK REFERENCE CARD

### Advanced Bash Commands

| Feature | Syntax | Example |
|---------|--------|---------|
| Strict mode | `set -euo pipefail` | Start of script |
| Trap signal | `trap 'cmd' SIG` | `trap 'cleanup' EXIT` |
| Regex match | `[[ $s =~ r ]]` | `[[ $s =~ ^[0-9]+$ ]]` |
| Capture group | `${BASH_REMATCH[n]}` | Extract matched parts |
| Process sub in | `<(command)` | `diff <(ls a) <(ls b)` |
| Process sub out | `>(command)` | `tee >(cmd) > file` |
| Here doc | `<< EOF ... EOF` | Multi-line text |
| Here string | `<<< "string"` | Single line input |
| getopts | `getopts "f:" opt` | Parse options |

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always use `set -euo pipefail` at the start of production scripts for robust error handling.

> 💡 **Pro Tip #2:** Use `trap` for cleanup - it runs even if your script fails or is interrupted.

> 💡 **Pro Tip #3:** Process substitution `<(command)` is more efficient than temporary files.

> 💡 **Pro Tip #4:** Use here documents with quoted delimiter `<< 'EOF'` to prevent variable expansion when needed.

> 💡 **Pro Tip #5:** Always validate user input before using it in commands to prevent injection attacks.

> 💡 **Pro Tip #6:** Use `mktemp` for temporary files - it creates unique files securely.

> 💡 **Pro Tip #7:** Combine `grep`, `sed`, and `awk` for powerful text processing pipelines.

> 💡 **Pro Tip #8:** Use `getopts` for simple option parsing, external libraries for complex CLI apps.

> 💡 **Pro Tip #9:** Quote all variables in regex comparisons: `[[ "$var" =~ $regex ]]`.

> 💡 **Pro Tip #10:** Test scripts with `shellcheck` before deployment to catch common mistakes.

---

## 🔥 REAL WORLD APPLICATIONS

### Where Advanced Bash Scripting Applies

**1. DevOps Automation**
- CI/CD pipeline scripts
- Infrastructure provisioning
- Deployment automation
- Monitoring and alerting

**2. Security Tools**
- Log analysis scripts
- Intrusion detection
- Vulnerability scanning
- Incident response automation

**3. Data Processing**
- ETL pipelines
- Log parsing and analysis
- Report generation
- Data transformation

**4. System Administration**
- Backup automation
- User management
- Service monitoring
- Configuration management

**5. Development Tools**
- Build scripts
- Test automation
- Code generation
- Development environment setup

---

## 🏆 BONUS: ADVANCED TIPS

### Performance Optimization

```bash
# Avoid subshells in loops
# Slow:
for f in $(ls); do ... done

# Fast:
for f in *; do ... done

# Use builtins over external commands
# Slow:
output=$(echo "$var" | sed 's/old/new/')

# Fast:
output="${var/old/new}"

# Minimize forks
# Slow:
for i in {1..100}; do
    echo "$i"
done | cat

# Fast:
for i in {1..100}; do
    echo "$i"
done
```

### Debugging Techniques

```bash
# Enable debugging
set -x  # Show commands
set -v  # Show input lines
set -n  # Check syntax only

# Debug specific section
set -x
# code to debug
set +x

# Trace with line numbers
PS4='+ ${BASH_SOURCE}:${LINENO}: ' set -x

# Use bashdb for step-by-step debugging
# pkg install bashdb
# bashdb script.sh
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ Error handling with set options and trap
- ✅ Signal handling for graceful shutdowns
- ✅ Regular expressions in Bash
- ✅ Process substitution for advanced pipelines
- ✅ Here documents and here strings
- ✅ Advanced text processing with sed/awk
- ✅ Building professional CLI tools
- ✅ Security best practices

### Key Takeaways

1. **Always use strict mode** - `set -euo pipefail` catches many errors
2. **Handle signals properly** - Graceful shutdown is professional
3. **Validate all input** - Security depends on it
4. **Use the right tool** - sed/awk/grep each have strengths
5. **Test thoroughly** - shellcheck and debugging tools help

---

## 🎯 INTERVIEW QUESTIONS

**Q1: Explain `set -euo pipefail` and why it's important.**

```bash
# Answer:
set -e    # Exit immediately if a command exits with non-zero status
set -u    # Treat unset variables as an error when substituting
set -o pipefail  # Return value of pipeline is the rightmost command to exit with non-zero

# Importance: Makes scripts fail fast and predictably
# Without it, scripts continue after errors, causing unexpected behavior
```

**Q2: How does trap work? Give examples.**

```bash
# Answer: trap registers commands to run on signals

# Cleanup on exit
trap 'rm -f $TEMP_FILE' EXIT

# Handle Ctrl+C gracefully
trap 'echo "Interrupted"; exit 130' INT

# Multiple signals
trap 'cleanup' EXIT INT TERM

# Debug mode
trap 'echo "Line $LINENO: $BASH_COMMAND"' DEBUG
```

**Q3: Explain process substitution with examples.**

```bash
# Answer: Process substitution treats command output as a file

# Input substitution <()
diff <(sort file1) <(sort file2)

# Output substitution >()
tee >(process1) >(process2) > output

# In loops
while read line; do
    process "$line"
done < <(grep pattern file.txt)
```

**Q4: What is the difference between `[ ]` and `[[ ]]`?**

```bash
# Answer:
# [ ] - POSIX test command, limited features
# [[ ]] - Bash extended test, more features

# [[ ]] advantages:
[[ $str == pattern* ]]     # Pattern matching
[[ $str =~ regex ]]        # Regex support
[[ $a > $b ]]             # No escaping needed
[[ -f $file ]]            # No quoting needed
```

**Q5: How do here documents work?**

```bash
# Answer: Here documents provide multi-line input

# Basic
cat << EOF
Line 1
Line 2
EOF

# No variable expansion
cat << 'EOF'
$HOME won't expand
EOF

# To file
cat > file.txt << EOF
Content here
EOF

# To function
pass_to_func() { cat; }
pass_to_func << EOF
Input data
EOF
```

---

## 🚀 BEST PRACTICES

### Code Style

```bash
# Good: Use meaningful names
validate_email() { ... }
process_log_file() { ... }

# Good: Use constants
readonly MAX_RETRIES=5
readonly LOG_FILE="/var/log/script.log"

# Good: Quote everything
[[ "$variable" == "value" ]]

# Good: Check return values
if ! command; then
    handle_error
fi
```

### Security Guidelines

```bash
# 1. Validate input
validate() {
    [[ "$1" =~ ^[a-zA-Z0-9]+$ ]] || return 1
}

# 2. Use secure temp files
TEMP=$(mktemp) || exit 1
trap 'rm -f "$TEMP"' EXIT

# 3. Avoid injection
# Bad: eval "$user_input"
# Good: Use arrays or direct commands

# 4. Set permissions
umask 077

# 5. Use full paths for critical operations
/bin/rm -f "$file"
```

---

## 📊 CODE COMPARISON

### Before vs After: Error Handling

```bash
# ❌ BEFORE: No error handling
#!/bin/bash
cd /some/path
rm -rf *
echo "Done"

# ✅ AFTER: Robust error handling
#!/usr/bin/env bash
set -euo pipefail

cleanup() {
    log "Cleanup on exit"
}
trap cleanup EXIT

log() { echo "[$(date)] $*"; }
die() { echo "ERROR: $*" >&2; exit 1; }

target="/some/path"
[[ -d "$target" ]] || die "Directory not found: $target"

log "Processing..."
cd "$target" || die "Cannot cd to $target"
# ... rest of script
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relevance |
|---------|-------|-----------|
| Chapter 11 | Python Installation | Alternative scripting |
| Chapter 12 | Python Basics | Compare with Bash |
| Chapter 13 | Bash Basics | Prerequisite |
| Chapter 15 | Git Version Control | Version scripts |
| Chapter 25 | Automation Scripts | Practical applications |

---

## 🎮 INTERACTIVE QUIZ

**1. What does `set -e` do?**
- A) Enables echo
- B) Exits on command failure
- C) Enables debugging
- D) Sets environment

<details>
<summary>Answer</summary>
**B) Exits on command failure** - Script stops immediately if any command returns non-zero exit status.
</details>

**2. Which trap catches Ctrl+C?**
- A) `trap 'cmd' EXIT`
- B) `trap 'cmd' TERM`
- C) `trap 'cmd' INT`
- D) `trap 'cmd' HUP`

<details>
<summary>Answer</summary>
**C) `trap 'cmd' INT`** - SIGINT is sent when user presses Ctrl+C.
</details>

**3. What does `< <(command)` do?**
- A) Redirects input
- B) Process substitution
- C) Here document
- D) Output redirection

<details>
<summary>Answer</summary>
**B) Process substitution** - Creates a temporary file from command output and provides its path.
</details>

**4. Which is the correct here document syntax?**
- A) `cat < EOF ... EOF`
- B) `cat << EOF ... EOF`
- C) `cat <<< EOF ... EOF`
- D) `cat > EOF ... EOF`

<details>
<summary>Answer</summary>
**B) `cat << EOF ... EOF`** - `<<` starts a here document, followed by delimiter.
</details>

---

## 🔧 DEBUG THIS EXERCISES

### Debug This #1: Trap Not Working

```bash
# Problem: Cleanup not running on error
#!/bin/bash
trap 'rm -f $TEMP' EXIT
TEMP=$(mktemp)
exit 1
# Temp file not deleted!
```

<details>
<summary>Solution</summary>

```bash
# Solution: Trap catches EXIT but file path needs quoting
#!/bin/bash
trap 'rm -f "$TEMP"' EXIT
TEMP=$(mktemp)
echo "Temp: $TEMP"
exit 1
# Now cleanup works!
```
</details>

### Debug This #2: Regex Not Matching

```bash
# Problem: Always returns false
email="test@example.com"
[[ $email =~ ^[a-z]+@[a-z]+\.[a-z]+$ ]]
echo $?
```

<details>
<summary>Solution</summary>

```bash
# Solution: Store regex in variable or quote properly
email="test@example.com"
regex="^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"
[[ $email =~ $regex ]]
echo $?  # 0 = match
```
</details>

---

## 💻 CODING CHALLENGES

### Challenge 1: Log Analyzer with Regex

Create a script that parses log files and extracts errors with timestamps.

```bash
#!/bin/bash
# Challenge: Parse logs and extract:
# 1. All ERROR lines with timestamps
# 2. Unique error messages
# 3. Error count per hour
```

<details>
<summary>Solution</summary>

```bash
#!/bin/bash
set -euo pipefail

LOG_FILE="${1:-}"

analyze_errors() {
    echo "=== Error Analysis ==="
    
    # Extract errors with timestamps
    grep -E "ERROR" "$LOG_FILE" | while read -r line; do
        timestamp=$(echo "$line" | grep -oE '[0-9]{4}-[0-9]{2}-[0-9]{2} [0-9]{2}:[0-9]{2}:[0-9]{2}')
        echo "[$timestamp] $line"
    done
    
    echo ""
    echo "=== Unique Errors ==="
    grep "ERROR" "$LOG_FILE" | sed 's/ERROR: //' | sort -u
    
    echo ""
    echo "=== Errors Per Hour ==="
    grep "ERROR" "$LOG_FILE" | \
        grep -oE '[0-9]{2}:[0-9]{2}' | \
        cut -d: -f1 | \
        sort | uniq -c | sort -rn
}

analyze_errors "$LOG_FILE"
```
</details>

### Challenge 2: Process Manager

Create a script that manages multiple background processes.

```bash
#!/bin/bash
# Challenge: Create a process manager that:
# 1. Starts multiple workers
# 2. Monitors their health
# 3. Restarts failed workers
# 4. Provides status reporting
```

<details>
<summary>Solution</summary>

```bash
#!/bin/bash
set -euo pipefail

declare -A WORKERS
MAX_WORKERS=3
LOG_FILE="/tmp/process_manager.log"

log() { echo "[$(date '+%Y-%m-%d %H:%M:%S')] $*" | tee -a "$LOG_FILE"; }

start_worker() {
    local id=$1
    (
        while true; do
            log "Worker $id: Working..."
            sleep $((RANDOM % 10 + 5))
        done
    ) &
    WORKERS[$id]=$!
    log "Started worker $id with PID ${WORKERS[$id]}"
}

check_workers() {
    for id in "${!WORKERS[@]}"; do
        if ! kill -0 "${WORKERS[$id]}" 2>/dev/null; then
            log "Worker $id died, restarting..."
            start_worker "$id"
        fi
    done
}

# Cleanup on exit
cleanup() {
    log "Shutting down..."
    for pid in "${WORKERS[@]}"; do
        kill "$pid" 2>/dev/null || true
    done
}
trap cleanup EXIT

# Start workers
for i in $(seq 1 $MAX_WORKERS); do
    start_worker "$i"
done

# Monitor loop
log "Process manager running..."
while true; do
    sleep 5
    check_workers
done
```
</details>

---

*Created by T3rmuxk1ng | Termux Full Course*

---

## 🎮 INTERACTIVE QUIZ

### Test Your Advanced Bash Knowledge!

**Q1: What does `set -euo pipefail` do?**
- A) Enables debugging
- B) Sets strict mode for scripts
- C) Configures pipe settings
- D) Sets environment variables

<details>
<summary>Answer</summary>
**B) Sets strict mode for scripts** - Combines: `-e` (exit on error), `-u` (error on undefined vars), `-o pipefail` (pipe fails on any error).
</details>

---

**Q2: What is process substitution `<()` used for?**
- A) File redirection
- B) Treating command output as a file
- C) Creating processes
- D) Input validation

<details>
<summary>Answer</summary>
**B) Treating command output as a file** - Allows command output to be used where a file path is expected.
</details>

---

**Q3: What signal does Ctrl+C send?**
- A) SIGTERM
- B) SIGKILL
- C) SIGINT
- D) SIGHUP

<details>
<summary>Answer</summary>
**C) SIGINT** - Interrupt signal (signal 2), can be caught and handled with trap.
</details>

---

**Q4: How do you capture regex groups in Bash?**
- A) `grep -o`
- B) `BASH_REMATCH`
- C) `sed -r`
- D) All of the above

<details>
<summary>Answer</summary>
**D) All of the above** - `BASH_REMATCH` for `[[ =~ ]]`, `grep -o` for extraction, `sed -r` for replacement.
</details>

---

**Q5: What is a here document?**
- A) A documentation file
- B) Multi-line input redirection
- C) A help command
- D) Configuration file

<details>
<summary>Answer</summary>
**B) Multi-line input redirection** - Uses `<< EOF ... EOF` to provide multi-line text as input.
</details>

---

**Q6: Which command creates a named pipe?**
- A) `pipe`
- B) `mkfifo`
- C) `mknod`
- D) Both B and C

<details>
<summary>Answer</summary>
**D) Both B and C** - `mkfifo` is the standard command, `mknod p` also works.
</details>

---

**Q7: What does `$BASH_REMATCH` contain?**
- A) Previous command
- B) Regex match groups
- C) Command history
- D) Variable values

<details>
<summary>Answer</summary>
**B) Regex match groups** - After `[[ $string =~ regex ]]`, contains matched groups.
</details>

---

**Q8: How do you run a command in the background?**
- A) `bg command`
- B) `command &`
- C) `run command`
- D) `start command`

<details>
<summary>Answer</summary>
**B) `command &`** - The ampersand runs the command in background. Use `bg` to resume a stopped job.
</details>

---

**Q9: What does `trap` do?**
- A) Catches signals
- B) Debugs scripts
- C) Creates variables
- D) Handles errors only

<details>
<summary>Answer</summary>
**A) Catches signals** - `trap` registers commands to execute on signals (EXIT, INT, TERM, etc.).
</details>

---

**Q10: What is `$!`?**
- A) Last argument
- B) PID of last background command
- C) Exit status
- D) Current process ID

<details>
<summary>Answer</summary>
**B) PID of last background command** - Useful for monitoring background processes.
</details>

---

**Q11: How do you make a here document NOT expand variables?**
- A) `<< 'EOF'`
- B) `<< "EOF"`
- C) `<<\EOF`
- D) `<<- EOF`

<details>
<summary>Answer</summary>
**A) `<< 'EOF'`** - Quoting the delimiter prevents variable expansion.
</details>

---

**Q12: What does `exec` do?**
- A) Executes a command
- B) Replaces current shell
- C) Both A and B
- D) Creates a subshell

<details>
<summary>Answer</summary>
**C) Both A and B** - Can redirect file descriptors or replace shell with a command.
</details>

---

## 💡 PRO TIPS

### 10 Advanced Bash Pro Tips

> **💡 Pro Tip #1: Use `trap` for Cleanup**
> Always clean up resources:
> ```bash
> TEMP_FILE=$(mktemp)
> trap 'rm -f "$TEMP_FILE"' EXIT
> # Script continues...
> ```

> **💡 Pro Tip #2: Debug with LINENO**
> Know where errors occur:
> ```bash
> trap 'echo "Error at line $LINENO: $BASH_COMMAND"' ERR
> ```

> **💡 Pro Tip #3: Use `exec` for Redirection**
> Redirect all output in one place:
> ```bash
> exec > >(tee -a log.txt) 2>&1
> # All output goes to both stdout and log.txt
> ```

> **💡 Pro Tip #4: Lock Files for Single Instance**
> Prevent multiple instances:
> ```bash
> LOCK_FILE="/tmp/script.lock"
> exec 200>"$LOCK_FILE"
> flock -n 200 || exit 1
> ```

> **💡 Pro Tip #5: Timeout Commands**
> Don't hang forever:
> ```bash
> timeout 30s long_running_command
> ```

> **💡 Pro Tip #6: Parallel Processing**
> Speed up with parallel:
> ```bash
> find . -type f | parallel -j 4 process_file {}
> ```

> **💡 Pro Tip #7: Use Associative Arrays**
> Key-value storage:
> ```bash
> declare -A config
> config[host]="localhost"
> config[port]="8080"
> echo "${config[host]}:${config[port]}"
> ```

> **💡 Pro Tip #8: Color Logging**
> Professional output:
> ```bash
> log() { echo -e "\033[0;32m[$(date +%H:%M:%S)]\033[0m $*"; }
> error() { echo -e "\033[0;31m[ERROR]\033[0m $*" >&2; }
> ```

> **💡 Pro Tip #9: Safe String Operations**
> Avoid errors with defaults:
> ```bash
> name="${1:-default}"
> file="${config[file]:-"/etc/default.conf"}"
> ```

> **💡 Pro Tip #10: Use ShellCheck**
> Catch common mistakes:
> ```bash
> pkg install shellcheck
> shellcheck myscript.sh
> ```

---

## 🔥 REAL WORLD USE CASES

### Advanced Bash Scripts for Production

**Use Case #1: Service Manager**
```bash
#!/bin/bash
# service_manager.sh - Manage background services

set -euo pipefail

SERVICE_NAME="${1:-myapp}"
SERVICE_CMD="${2:-./app.sh}"
PID_FILE="/tmp/${SERVICE_NAME}.pid"
LOG_FILE="/tmp/${SERVICE_NAME}.log"

start() {
    if [ -f "$PID_FILE" ] && kill -0 $(cat "$PID_FILE") 2>/dev/null; then
        echo "Service already running"
        return 1
    fi
    
    nohup $SERVICE_CMD >> "$LOG_FILE" 2>&1 &
    echo $! > "$PID_FILE"
    echo "Started $SERVICE_NAME (PID: $(cat $PID_FILE))"
}

stop() {
    if [ -f "$PID_FILE" ]; then
        kill $(cat "$PID_FILE") 2>/dev/null || true
        rm -f "$PID_FILE"
        echo "Stopped $SERVICE_NAME"
    else
        echo "Service not running"
    fi
}

status() {
    if [ -f "$PID_FILE" ] && kill -0 $(cat "$PID_FILE") 2>/dev/null; then
        echo "Running (PID: $(cat $PID_FILE))"
    else
        echo "Stopped"
        rm -f "$PID_FILE"
    fi
}

case "${3:-}" in
    start) start ;;
    stop) stop ;;
    restart) stop; sleep 1; start ;;
    status) status ;;
    *) echo "Usage: $0 name command {start|stop|restart|status}" ;;
esac
```

**Use Case #2: Parallel File Processor**
```bash
#!/bin/bash
# parallel_processor.sh - Process files in parallel

set -euo pipefail

process_file() {
    local file="$1"
    local output="${file%.txt}_processed.txt"
    
    # Simulate processing
    echo "Processing: $file"
    sleep 1
    cat "$file" | tr 'a-z' 'A-Z' > "$output"
    echo "Done: $output"
}

export -f process_file

# Process all .txt files with 4 parallel jobs
find . -name "*.txt" -type f | parallel -j 4 process_file {}
```

**Use Case #3: Log Monitor with Alerts**
```bash
#!/bin/bash
# log_monitor.sh - Monitor logs and send alerts

set -euo pipefail

LOG_FILE="${1:-/var/log/app.log}"
PATTERNS=("ERROR" "CRITICAL" "FATAL")
ALERT_CMD="termux-notification --title 'Log Alert' --content"

tail -f "$LOG_FILE" | while read -r line; do
    for pattern in "${PATTERNS[@]}"; do
        if [[ "$line" == *"$pattern"* ]]; then
            echo "[$(date)] Found $pattern: $line"
            $ALERT_CMD "$pattern detected: ${line:0:50}..." 2>/dev/null || true
        fi
    done
done
```

**Use Case #4: Configuration Generator**
```bash
#!/bin/bash
# config_gen.sh - Generate config from template

set -euo pipefail

TEMPLATE="${1:-config.template}"
OUTPUT="${2:-config.conf}"

# Variables to substitute
HOST="${HOST:-localhost}"
PORT="${PORT:-8080}"
DB_HOST="${DB_HOST:-db.local}"
DB_PORT="${DB_PORT:-5432}"

# Generate config
envsubst < "$TEMPLATE" > "$OUTPUT"

echo "Generated: $OUTPUT"
```

**Use Case #5: Deployment Script**
```bash
#!/bin/bash
# deploy.sh - Zero-downtime deployment

set -euo pipefail

APP_NAME="${1:-myapp}"
DEPLOY_DIR="/var/www/$APP_NAME"
BACKUP_DIR="/var/backups/$APP_NAME"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

log() { echo "[$(date +%H:%M:%S)] $*"; }

# Backup current version
backup() {
    log "Creating backup..."
    mkdir -p "$BACKUP_DIR"
    tar -czf "$BACKUP_DIR/backup_$TIMESTAMP.tar.gz" -C "$DEPLOY_DIR" .
}

# Deploy new version
deploy() {
    log "Deploying new version..."
    
    # Pull latest code
    cd "$DEPLOY_DIR"
    git pull origin main
    
    # Install dependencies
    pip install -r requirements.txt --quiet
    
    # Run migrations
    python manage.py migrate --noinput
    
    # Restart service
    systemctl restart "$APP_NAME" || true
}

# Rollback on failure
rollback() {
    log "Rolling back..."
    latest_backup=$(ls -t "$BACKUP_DIR"/*.tar.gz | head -1)
    tar -xzf "$latest_backup" -C "$DEPLOY_DIR"
    systemctl restart "$APP_NAME" || true
}

# Main deployment
trap rollback ERR

backup
deploy

log "Deployment successful!"
trap - ERR
```

---

## ⚡ QUICK REFERENCE CARD

### Signal Handling

| Signal | Number | Description | Catchable |
|--------|--------|-------------|-----------|
| SIGINT | 2 | Ctrl+C | Yes |
| SIGTERM | 15 | Graceful stop | Yes |
| SIGKILL | 9 | Force kill | No |
| SIGHUP | 1 | Hangup | Yes |
| SIGSTOP | 19 | Pause | No |
| SIGCONT | 18 | Resume | Yes |

### trap Examples

```bash
# Cleanup on exit
trap 'rm -f $TEMP_FILE' EXIT

# Handle Ctrl+C
trap 'echo "Interrupted"; exit 130' INT

# Multiple signals
trap 'cleanup' EXIT INT TERM

# Debug mode
trap 'echo "Line $LINENO: $BASH_COMMAND"' DEBUG

# Error handler
trap 'error "Failed at line $LINENO"' ERR
```

### Process Substitution

```bash
# Input substitution
diff <(sort file1) <(sort file2)

# Output substitution
tee >(process1) >(process2) > output

# In loops
while read line; do
    echo "$line"
done < <(grep pattern file.txt)
```

### Here Documents & Strings

```bash
# Here document (expands variables)
cat << EOF
Hello, $USER!
EOF

# Here document (no expansion)
cat << 'EOF'
Hello, $USER!  # Literal output
EOF

# Here string
grep pattern <<< "search this string"

# With indentation
cat <<- EOF
    Indented content
    is allowed
EOF
```

### Regex in Bash

```bash
# Match test
[[ "$string" =~ pattern ]]

# Capture groups
[[ "user@domain.com" =~ ^(.+)@(.+)$ ]]
echo "${BASH_REMATCH[1]}"  # user
echo "${BASH_REMATCH[2]}"  # domain.com

# Common patterns
IP='^([0-9]{1,3}\.){3}[0-9]{1,3}$'
EMAIL='^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}$'
```

---

## 🏆 BONUS CONTENT

### Professional Script Framework

```bash
#!/usr/bin/env bash
#
# Professional Bash Script Framework
# A production-ready template with all best practices
#

# Exit settings
set -euo pipefail
IFS=$'\n\t'

# Script info
readonly SCRIPT_NAME=$(basename "$0")
readonly SCRIPT_VERSION="2.0.0"
readonly SCRIPT_DIR=$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)

# Logging configuration
declare -A LOG_LEVELS=([DEBUG]=0 [INFO]=1 [WARN]=2 [ERROR]=3)
LOG_LEVEL="INFO"
LOG_FILE=""

# Color codes
declare -A COLORS=(
    [RED]='\033[0;31m'
    [GREEN]='\033[0;32m'
    [YELLOW]='\033[0;33m'
    [BLUE]='\033[0;34m'
    [NC]='\033[0m'
)

# Logging function
log() {
    local level="${1:-INFO}"
    shift
    local message="$*"
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    
    if [[ ${LOG_LEVELS[$level]} -ge ${LOG_LEVELS[$LOG_LEVEL]} ]]; then
        local color="${COLORS[$level]:-${COLORS[NC]}}"
        echo -e "${color}[$timestamp] [$level]${COLORS[NC]} $message"
        
        if [[ -n "$LOG_FILE" ]]; then
            echo "[$timestamp] [$level] $message" >> "$LOG_FILE"
        fi
    fi
}

# Error handling
error_exit() {
    log "ERROR" "$1"
    exit "${2:-1}"
}

# Cleanup function
cleanup() {
    local exit_code=$?
    log "DEBUG" "Cleanup triggered (exit code: $exit_code)"
    # Add cleanup tasks here
    exit $exit_code
}
trap cleanup EXIT

# Signal handlers
handle_interrupt() {
    echo ""
    log "WARN" "Operation cancelled by user"
    exit 130
}
trap handle_interrupt INT TERM

# Argument parser
parse_args() {
    local help_text="
Usage: ${SCRIPT_NAME} [OPTIONS] <arguments>

Options:
    -h, --help          Show this help
    -v, --version       Show version
    -d, --debug         Enable debug mode
    -q, --quiet         Suppress output
    -l, --log FILE      Log to file

Examples:
    ${SCRIPT_NAME} example
    ${SCRIPT_NAME} -d --log app.log example
"
    
    while [[ $# -gt 0 ]]; do
        case "$1" in
            -h|--help) echo "$help_text"; exit 0 ;;
            -v|--version) echo "${SCRIPT_NAME} v${SCRIPT_VERSION}"; exit 0 ;;
            -d|--debug) LOG_LEVEL="DEBUG"; set -x ;;
            -q|--quiet) LOG_LEVEL="ERROR" ;;
            -l|--log) LOG_FILE="$2"; shift ;;
            --) shift; break ;;
            -*) error_exit "Unknown option: $1" ;;
            *) break ;;
        esac
        shift
    done
}

# Dependency checker
check_dependencies() {
    local deps=("$@")
    for dep in "${deps[@]}"; do
        if ! command -v "$dep" &>/dev/null; then
            error_exit "Required dependency not found: $dep"
        fi
    done
}

# Lock file management
acquire_lock() {
    local lock_file="${1:-/tmp/${SCRIPT_NAME}.lock}"
    exec 200>"$lock_file"
    flock -n 200 || error_exit "Another instance is already running"
}

# Main function
main() {
    parse_args "$@"
    
    log "INFO" "Starting ${SCRIPT_NAME} v${SCRIPT_VERSION}"
    log "DEBUG" "Script directory: ${SCRIPT_DIR}"
    
    # Check dependencies
    check_dependencies git curl jq
    
    # Your code here
    log "INFO" "Processing..."
    
    log "INFO" "Completed successfully"
}

# Run main
main "$@"
```

---

## 📝 CHAPTER SUMMARY

### Key Takeaways

| Topic | Key Points |
|-------|------------|
| **Error Handling** | `set -euo pipefail`, check `$?` |
| **Signals** | INT, TERM, HUP - handle with trap |
| **trap** | Cleanup, signal handling, error recovery |
| **Regex** | `[[ =~ ]]`, `BASH_REMATCH` |
| **Process Sub** | `<()` input, `>()` output |
| **Here Docs** | Multi-line text, `<< EOF` |
| **Named Pipes** | `mkfifo`, IPC mechanism |
| **CLI Tools** | `getopts`, argument parsing |
| **Security** | Validate input, avoid eval |

### Essential Patterns

```bash
# Strict mode
set -euo pipefail

# Cleanup
trap 'rm -f "$tmp"' EXIT

# Process substitution
diff <(cmd1) <(cmd2)

# Here document
cat << EOF
$content
EOF

# Regex matching
[[ $str =~ ^[0-9]+$ ]]

# Background process management
cmd &
PID=$!
wait $PID
```

---

## 🎯 INTERVIEW QUESTIONS

### Advanced Bash Interview Questions

**Q1: Explain how `trap` works with EXIT.**

<details>
<summary>Answer</summary>
`trap 'command' EXIT` registers a command to run when the shell exits, regardless of how (success, error, signal). Useful for cleanup.

```bash
cleanup() { rm -f "$TEMP_FILE"; }
trap cleanup EXIT
# cleanup runs even if script fails
```
</details>

**Q2: What is the difference between `wait` and `wait $PID`?**

<details>
<summary>Answer</summary>
- `wait`: Waits for ALL background jobs to complete
- `wait $PID`: Waits for specific process

```bash
process1 &
PID1=$!
process2 &
PID2=$!

wait $PID1  # Wait for process1
# process2 might still be running
wait        # Wait for all remaining
```
</details>

**Q3: How do you implement a timeout for a command?**

<details>
<summary>Answer</summary>
```bash
# Method 1: timeout command
timeout 30s long_command

# Method 2: Manual implementation
command &
PID=$!
(sleep 30; kill $PID 2>/dev/null) &
WATCHDOG=$!
wait $PID
kill $WATCHDOG 2>/dev/null
```
</details>

**Q4: Explain named pipes (FIFOs).**

<details>
<summary>Answer</summary>
Named pipes are special files that allow inter-process communication.

```bash
# Create FIFO
mkfifo mypipe

# Writer (blocks until reader)
echo "data" > mypipe &

# Reader
cat < mypipe  # Gets "data"

# Cleanup
rm mypipe
```
</details>

**Q5: How do you handle concurrent access to a script?**

<details>
<summary>Answer</summary>
```bash
# Using flock for locking
LOCK_FILE="/tmp/script.lock"
exec 200>"$LOCK_FILE"
flock -n 200 || { echo "Already running"; exit 1; }
# Script continues with exclusive lock
```
</details>

---

## 🚀 BEST PRACTICES

### Production Script Checklist

```bash
# ✅ Header
#!/usr/bin/env bash
# Description, Author, Version

# ✅ Strict mode
set -euo pipefail

# ✅ Constants (readonly)
readonly SCRIPT_NAME=$(basename "$0")

# ✅ Cleanup
trap cleanup EXIT

# ✅ Logging
log() { echo "[$(date)] $*" >&2; }

# ✅ Error handling
error() { log "ERROR: $*"; exit 1; }

# ✅ Dependency check
command -v curl &>/dev/null || error "curl required"

# ✅ Help/Usage
usage() { cat << EOF ...; }

# ✅ Argument parsing
parse_args() { ... }

# ✅ Main function
main() { ... }
main "$@"
```

### Common Pitfalls

| ❌ Pitfall | ✅ Solution |
|-----------|------------|
| No error handling | Use `set -e` |
| Unquoted variables | Quote everything |
| No cleanup | Use `trap` |
| Blocking scripts | Use timeouts |
| Race conditions | Use locks |
| No logging | Add log function |

---

## 📊 CODE COMPARISON

### Bad vs Good: Error Handling

```bash
# ❌ BAD: No error handling
#!/bin/bash
cd /some/path
rm -rf *
echo "Done"

# ✅ GOOD: Comprehensive error handling
#!/usr/bin/env bash
set -euo pipefail

cleanup() {
    log "Cleanup..."
}
trap cleanup EXIT

log() { echo "[$(date)] $*" >&2; }
error() { log "ERROR: $*"; exit 1; }

cd /some/path || error "Cannot cd to /some/path"
# More cautious about rm -rf
find . -type f -name "*.tmp" -delete
log "Done"
```

### Bad vs Good: Process Management

```bash
# ❌ BAD: Fire and forget
process1 &
process2 &
process3 &
# Don't know if they succeeded

# ✅ GOOD: Monitor processes
pids=()

process1 & pids+=($!)
process2 & pids+=($!)
process3 & pids+=($!)

# Wait and check all
for pid in "${pids[@]}"; do
    if ! wait $pid; then
        echo "Process $pid failed"
        exit 1
    fi
done
```

---

## 🔗 RELATED CHAPTERS

### Prerequisites
- **Chapter 13**: Bash Scripting Basics ← Start here if new to Bash

### Next Steps
- **Chapter 17**: Termux API Scripts
- **Chapter 22**: Automation Scripts
- **Chapter 27**: Security Tools Development

### Related Programming
- **Chapter 11**: Python Installation
- **Chapter 12**: Python Basics
- **Chapter 16**: Node.js in Termux

---

*Updated by T3rmuxk1ng | Termux Full Course - Module 3: Programming*
