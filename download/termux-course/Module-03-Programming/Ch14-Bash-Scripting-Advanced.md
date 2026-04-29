```
 ██████╗ █████╗ ██╗     ██╗     ██████╗  █████╗ ███╗   ███╗███████╗███████╗████████╗███████╗██████╗ 
██╔════╝██╔══██╗██║     ██║     ██╔══██╗██╔══██╗████╗ ████║██╔════╝██╔════╝╚══██╔══╝██╔════╝██╔══██╗
██║     ███████║██║     ██║     ██████╔╝███████║██╔████╔██║█████╗  ███████╗   ██║   █████╗  ██████╔╝
██║     ██╔══██║██║     ██║     ██╔══██╗██╔══██║██║╚██╔╝██║██╔══╝  ╚════██║   ██║   ██╔══╝  ██╔══██╗
╚██████╗██║  ██║███████╗███████╗██║  ██║██║  ██║██║ ╚═╝ ██║███████╗███████║   ██║   ███████╗██║  ██║
 ╚═════╝╚═╝  ╚═╝╚══════╝╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚══════╝╚══════╝   ╚═╝   ╚══════╝╚═╝  ╚═╝
                                                                                                    
 █████╗ ███████╗ ██████╗██╗██╗    ████████╗██╗  ██╗███████╗    ██████╗ ██████╗ ███████╗███████╗██████╗ 
██╔══██╗██╔════╝██╔════╝██║██║    ╚══██╔══╝██║  ██║██╔════╝   ██╔════╝██╔═══██╗██╔════╝██╔════╝██╔══██╗
███████║███████╗██║     ██║██║       ██║   ███████║█████╗     ██║     ██║   ██║█████╗  █████╗  ██████╔╝
██╔══██║╚════██║██║     ██║██║       ██║   ██╔══██║██╔══╝     ██║     ██║   ██║██╔══╝  ██╔══╝  ██╔══██╗
██║  ██║███████║╚██████╗██║███████╗  ██║   ██║  ██║███████╗   ╚██████╗╚██████╔╝███████╗███████╗██║  ██║
╚═╝  ╚═╝╚══════╝ ╚═════╝╚═╝╚══════╝  ╚═╝   ╚═╝  ╚═╝╚══════╝    ╚═════╝ ╚═════╝ ╚══════╝╚══════╝╚═╝  ╚═╝
```

# 🚀 Chapter 14: Advanced Bash Scripting

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

## 🎮 INTERACTIVE QUIZ

Test your Advanced Bash Scripting knowledge! Click to reveal answers.

<details>
<summary><b>Q1: What does set -euo pipefail do?</b></summary>

This is the "strict mode" for Bash scripts that catches many common errors:

```bash
#!/bin/bash
set -e    # Exit immediately if any command fails
set -u    # Error when using undefined variables
set -o pipefail  # Pipeline fails if any command in it fails

# Combined as:
set -euo pipefail

# Why use it?
# - Makes scripts more reliable
# - Catches errors early
# - Prevents silent failures
# - Production-ready scripts
```
</details>

<details>
<summary><b>Q2: How does trap work and what signals can it catch?</b></summary>

`trap` registers commands to execute when signals are received:

```bash
# Common signals:
# EXIT  - Script exit (pseudo-signal, always runs)
# INT   - Ctrl+C interrupt
# TERM  - Termination request
# HUP   - Hangup (terminal closed)
# ERR   - Command error (with set -e)

# Basic trap
trap 'echo "Cleaning up..."; rm -f $temp' EXIT

# Multiple signals
trap 'cleanup' EXIT INT TERM

# Ignore a signal
trap '' INT  # Ignore Ctrl+C

# Practical example
cleanup() {
    echo "Removing temp files..."
    rm -f /tmp/myapp_*
}
trap cleanup EXIT
```
</details>

<details>
<summary><b>Q3: What's the difference between <() and >() process substitution?</b></summary>

Process substitution treats command output/input as a file:

```bash
# Input substitution <() - Output as file
diff <(sort file1.txt) <(sort file2.txt)
# Bash creates temporary file descriptors

# Use in loops
while read line; do
    process "$line"
done < <(grep "error" log.txt)

# Output substitution >() - Input as file
tee >(process1) >(process2) > output.txt

# Practical: Compare directory contents
diff <(ls -a dir1 | sort) <(ls -a dir2 | sort)
```
</details>

<details>
<summary><b>Q4: How do you use regex in Bash with =~?</b></summary>

The `=~` operator enables regex matching in `[[ ]]`:

```bash
# Basic regex match
[[ "hello123" =~ [0-9]+ ]] && echo "Has numbers"

# Extract capture groups
url="https://example.com/path"
if [[ $url =~ ^(https?)://([^/]+)(/.*)?$ ]]; then
    echo "Protocol: ${BASH_REMATCH[1]}"  # https
    echo "Domain: ${BASH_REMATCH[2]}"     # example.com
    echo "Path: ${BASH_REMATCH[3]}"       # /path
fi

# Email validation
validate_email() {
    [[ $1 =~ ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$ ]]
}

# IP address check
is_ip() {
    [[ $1 =~ ^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}$ ]]
}
```
</details>

<details>
<summary><b>Q5: What's a here document and how do you use it?</b></summary>

Here documents provide multi-line text input:

```bash
# Basic here-doc
cat << EOF
Line 1
Line 2
Variables work: $HOME
EOF

# Quoted delimiter - no expansion
cat << 'EOF'
Variables NOT expanded: $HOME
Commands NOT run: $(date)
EOF

# To file
cat > config.txt << EOF
setting=value
port=8080
EOF

# With indentation (strip tabs)
cat <<- EOF
    Indented content
    Tabs are removed
EOF

# In function
generate_html() {
    cat << EOF
<!DOCTYPE html>
<html><head><title>$1</title></head></html>
EOF
}
```
</details>

<details>
<summary><b>Q6: How do you use getopts for command-line argument parsing?</b></summary>

`getopts` parses short options in Bash scripts:

```bash
#!/bin/bash

usage() {
    echo "Usage: $0 [-v] [-f file] [-n num] args..."
    exit 1
}

verbose=false
file=""
number=0

# Parse options
while getopts "vf:n:" opt; do
    case $opt in
        v) verbose=true ;;
        f) file="$OPTARG" ;;
        n) number="$OPTARG" ;;
        \?) usage ;;
        :) echo "Option -$OPTARG requires argument"; usage ;;
    esac
done

# Shift past options
shift $((OPTIND-1))

# Remaining arguments in $@
echo "File: $file"
echo "Number: $number"
echo "Verbose: $verbose"
echo "Args: $@"
```
</details>

<details>
<summary><b>Q7: What is the difference between [ ] and [[ ]]?</b></summary>

`[[ ]]` is the Bash-enhanced test with more features:

```bash
# [ ] - POSIX test (portable)
[ "$var" = "value" ]        # Needs quoting
[ "$a" \< "$b" ]           # Must escape <
[ -z "$var" ]              # String tests

# [[ ]] - Bash extended test (recommended)
[[ $var == "value" ]]       # No quoting needed
[[ $var == pattern* ]]      # Pattern matching
[[ $var =~ ^[0-9]+$ ]]      # Regex support!
[[ $a < $b ]]              # No escaping

# Logical operators
[ $a -gt 5 ] && [ $a -lt 10 ]    # [ ] way
[[ $a -gt 5 && $a -lt 10 ]]      # [[ ]] way

# Use [[ ]] for Bash scripts, [ ] for POSIX compatibility
```
</details>

<details>
<summary><b>Q8: How do you create named pipes (FIFOs)?</b></summary>

Named pipes allow inter-process communication:

```bash
# Create named pipe
PIPE=/tmp/my_pipe_$$
mkfifo "$PIPE"

# Writer process (background)
(
    for i in {1..5}; do
        echo "Message $i" > "$PIPE"
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

# Practical: Parallel processing
mkfifo input_pipe output_pipe
producer > input_pipe &
consumer < output_pipe &
processor < input_pipe > output_pipe
```
</details>

<details>
<summary><b>Q9: What are here strings and how do they differ from here docs?</b></summary>

Here strings provide single-line input:

```bash
# Here string (<<<) - single line
grep "pattern" <<< "search in this string"

# Read into variables
read -r a b c <<< "one two three"
echo "$a, $b, $c"  # one, two, three

# With awk
awk '{print $2}' <<< "first second third"  # second

# Variable expansion
data="value1 value2 value3"
while read item; do
    echo "Item: $item"
done <<< "$data"

# Comparison:
# Here-doc: Multi-line, block text
# Here-string: Single line, quick input
```
</details>

<details>
<summary><b>Q10: How do you handle errors with trap and ERR signal?</b></summary>

Combine `set -e` with `trap` for comprehensive error handling:

```bash
#!/bin/bash
set -euo pipefail

# Error handler
error_handler() {
    local line=$1
    echo "ERROR: Script failed at line $line"
    echo "Command: $BASH_COMMAND"
    # Cleanup, logging, notifications
    cleanup
    exit 1
}

# Set trap for ERR
trap 'error_handler $LINENO' ERR

# Cleanup function
cleanup() {
    [[ -f "$TEMP_FILE" ]] && rm -f "$TEMP_FILE"
}

# Also trap EXIT for cleanup
trap cleanup EXIT

# Now any failed command triggers error_handler
# and cleanup always runs
```
</details>

<details>
<summary><b>Q11: What is BASH_REMATCH and how do you use it?</b></summary>

`BASH_REMATCH` stores regex capture groups:

```bash
# After =~ match, BASH_REMATCH contains captures
url="https://user:pass@example.com:8080/path?query=1"

# Parse URL components
regex='^(https?)://([^:]+):([^@]+)@([^:]+):([0-9]+)(/.*)$'

if [[ $url =~ $regex ]]; then
    echo "Protocol: ${BASH_REMATCH[1]}"  # https
    echo "User: ${BASH_REMATCH[2]}"      # user
    echo "Pass: ${BASH_REMATCH[3]}"      # pass
    echo "Host: ${BASH_REMATCH[4]}"      # example.com
    echo "Port: ${BASH_REMATCH[5]}"      # 8080
    echo "Path: ${BASH_REMATCH[6]}"      # /path?query=1
fi

# Index 0 = entire match
# Index 1+ = capture groups
```
</details>

<details>
<summary><b>Q12: How do you implement a progress indicator in Bash?</b></summary>

Multiple ways to show progress in scripts:

```bash
# Spinner
spinner() {
    local pid=$1
    local spin='-\|/'
    local i=0
    while kill -0 $pid 2>/dev/null; do
        i=$(( (i+1) % 4 ))
        printf "\r${spin:$i:1} Processing..."
        sleep 0.1
    done
    printf "\rDone!        \n"
}

# Progress bar
progress() {
    local current=$1
    local total=$2
    local width=50
    local percent=$((current * 100 / total))
    local filled=$((current * width / total))
    local empty=$((width - filled))
    printf "\r[%s%s] %d%%" \
        "$(printf '#%.0s' $(seq 1 $filled))" \
        "$(printf ' %.0s' $(seq 1 $empty))" \
        "$percent"
}

# Usage
for i in {1..100}; do
    progress $i 100
    sleep 0.05
done
echo
```
</details>

<details>
<summary><b>Q13: How do you create a locking mechanism in Bash?</b></summary>

Prevent multiple script instances from running simultaneously:

```bash
#!/bin/bash

LOCK_FILE="/tmp/my_script.lock"

# Acquire lock
acquire_lock() {
    # Try to create lock file atomically
    if ! (set -o noclobber; echo $$ > "$LOCK_FILE") 2>/dev/null; then
        echo "Script already running (PID: $(cat $LOCK_FILE))"
        exit 1
    fi
    trap 'rm -f "$LOCK_FILE"' EXIT
}

# Or using flock (more robust)
acquire_lock_flock() {
    exec 200>"$LOCK_FILE"
    flock -n 200 || {
        echo "Script already running"
        exit 1
    }
    # Lock is automatically released when script exits
}

# Usage
acquire_lock

# Main script
echo "Running script..."
sleep 10
echo "Done!"
```
</details>

<details>
<summary><b>Q14: How do you parse JSON in pure Bash?</b></summary>

While `jq` is recommended, here's pure Bash parsing:

```bash
# Simple JSON parsing with sed/grep
parse_json() {
    local json="$1"
    local key="$2"
    
    echo "$json" | sed -n "s/.*\"$key\"[[:space:]]*:[[:space:]]*\"\\([^\"]*\\)\".*/\\1/p"
}

# More robust with awk
json_get() {
    local json="$1"
    local key="$2"
    echo "$json" | awk -F"[,:}]" '{
        for(i=1;i<=NF;i++){
            if($i~/"'"$key"'"[[:space:]]*:/){
                print $(i+1)
            }
        }
    }' | tr -d ' "'
}

# Best: Use jq if available
if command -v jq &>/dev/null; then
    echo "$json" | jq -r '.key'
fi

# Example
json='{"name":"T3rmuxk1ng","age":25}'
parse_json "$json" "name"  # Output: T3rmuxk1ng
```
</details>

<details>
<summary><b>Q15: How do you implement timeouts for commands?</b></summary>

Run commands with timeouts in Bash:

```bash
# Using timeout command
timeout 5s ping google.com

# Check exit status
# 124 = timed out
# 0 = command succeeded
# other = command error

# Custom timeout function
run_with_timeout() {
    local timeout=$1
    shift
    local cmd="$@"
    
    (
        eval "$cmd" &
        local pid=$!
        (
            sleep "$timeout"
            kill $pid 2>/dev/null
        ) &
        wait $pid 2>/dev/null
    )
    
    return $?
}

# Using read with timeout
if read -t 5 -p "Quick! Press Enter: " </dev/tty; then
    echo "You made it!"
else
    echo "Too slow!"
fi
```
</details>

---

## 🎯 INTERVIEW QUESTIONS

### Top 10 Advanced Bash Interview Questions with Detailed Answers

**Q1: Explain the complete error handling strategy in Bash.**

```bash
#!/bin/bash
# Comprehensive error handling

# 1. Strict mode
set -euo pipefail

# 2. Trap for cleanup
cleanup() {
    local exit_code=$?
    echo "Cleanup on exit (code: $exit_code)"
    rm -f "$TEMP_FILE"
    # Add more cleanup
}
trap cleanup EXIT

# 3. Error handler
on_error() {
    local exit_code=$?
    local line_no=$1
    local command="$BASH_COMMAND"
    
    echo "ERROR at line $line_no: '$command'" >&2
    echo "Exit code: $exit_code" >&2
    
    # Log to file
    echo "[$(date)] ERROR at line $line_no: $command" >> error.log
    
    # Send notification
    # termux-notification --title "Script Error" --content "$command failed"
    
    exit $exit_code
}
trap 'on_error $LINENO' ERR

# 4. Interrupt handler
on_interrupt() {
    echo ""
    echo "Interrupted by user"
    exit 130
}
trap on_interrupt INT

# 5. Safe command execution
safe_exec() {
    "$@" || {
        echo "Command failed: $*" >&2
        return 1
    }
}

# 6. Validate inputs
validate() {
    [[ -n "$1" ]] || { echo "Argument required"; return 1; }
    [[ -f "$1" ]] || { echo "File not found: $1"; return 1; }
    [[ -r "$1" ]] || { echo "Cannot read: $1"; return 1; }
}

# Usage
TEMP_FILE=$(mktemp)
validate "$1"
safe_exec important_command "$1"
```

**Q2: How would you implement a job queue system in Bash?**

```bash
#!/bin/bash
# Job queue with parallel workers

QUEUE_FILE="/tmp/job_queue.txt"
MAX_WORKERS=4
declare -A WORKERS

# Add jobs to queue
add_job() {
    echo "$1" >> "$QUEUE_FILE"
}

# Process a single job
process_job() {
    local job="$1"
    echo "Processing: $job"
    # Simulate work
    sleep 2
    echo "Completed: $job"
}

# Worker function
worker() {
    local worker_id=$1
    while true; do
        # Get next job atomically
        job=$(flock -x "$QUEUE_FILE" -c "head -n1 '$QUEUE_FILE' && sed -i '1d' '$QUEUE_FILE'" 2>/dev/null)
        
        if [[ -z "$job" ]]; then
            break
        fi
        
        process_job "$job"
    done
}

# Start workers
start_workers() {
    for i in $(seq 1 $MAX_WORKERS); do
        worker $i &
        WORKERS[$i]=$!
    done
}

# Wait for all workers
wait_workers() {
    for pid in "${WORKERS[@]}"; do
        wait $pid
    done
}

# Main
add_job "task1"
add_job "task2"
add_job "task3"
add_job "task4"
add_job "task5"

start_workers
wait_workers

echo "All jobs completed!"
rm -f "$QUEUE_FILE"
```

**Q3: Implement a configuration management system.**

```bash
#!/bin/bash
# Configuration management system

# Default configuration
declare -A DEFAULTS=(
    ["server.host"]="localhost"
    ["server.port"]="8080"
    ["server.timeout"]="30"
    ["database.host"]="localhost"
    ["database.port"]="5432"
    ["database.name"]="myapp"
    ["log.level"]="INFO"
    ["log.file"]="/var/log/myapp.log"
)

declare -A CONFIG

# Load configuration file
load_config() {
    local config_file="${1:-config.ini}"
    
    if [[ -f "$config_file" ]]; then
        while IFS='=' read -r key value || [[ -n "$key" ]]; do
            # Skip comments and empty lines
            [[ "$key" =~ ^[[:space:]]*# || -z "$key" ]] && continue
            
            # Trim whitespace
            key=$(echo "$key" | xargs)
            value=$(echo "$value" | xargs)
            
            CONFIG[$key]="$value"
        done < "$config_file"
    fi
}

# Override with environment variables
load_env() {
    for key in "${!DEFAULTS[@]}"; do
        local env_key="APP_${key^^}"  # Convert to uppercase and prefix
        env_key=${env_key//./_}       # Replace dots with underscores
        
        if [[ -n "${!env_key:-}" ]]; then
            CONFIG[$key]="${!env_key}"
        fi
    done
}

# Get config value with default
get_config() {
    local key="$1"
    echo "${CONFIG[$key]:-${DEFAULTS[$key]}}"
}

# Set config value
set_config() {
    local key="$1"
    local value="$2"
    CONFIG[$key]="$value"
}

# Validate required configs
validate_config() {
    local required=("server.host" "server.port" "database.host")
    
    for key in "${required[@]}"; do
        if [[ -z "$(get_config "$key")" ]]; then
            echo "Required config missing: $key" >&2
            return 1
        fi
    done
}

# Save configuration
save_config() {
    local file="$1"
    > "$file"
    for key in "${!CONFIG[@]}"; do
        echo "$key=${CONFIG[$key]}" >> "$file"
    done
}

# Usage
load_config "myapp.conf"
load_env

echo "Server: $(get_config "server.host"):$(get_config "server.port")"
validate_config || exit 1
```

**Q4: Create a robust logging system.**

```bash
#!/bin/bash
# Logging system with levels, rotation, and multiple outputs

LOG_FILE="${LOG_FILE:-/var/log/script.log}"
LOG_LEVEL="${LOG_LEVEL:-INFO}"
LOG_MAX_SIZE="${LOG_MAX_SIZE:-10485760}"  # 10MB
LOG_MAX_FILES="${LOG_MAX_FILES:-5}"

# Log levels
declare -A LOG_LEVELS=(
    ["DEBUG"]=0
    ["INFO"]=1
    ["WARN"]=2
    ["ERROR"]=3
    ["FATAL"]=4
)

# Colors for terminal
declare -A LOG_COLORS=(
    ["DEBUG"]="\033[0;36m"  # Cyan
    ["INFO"]="\033[0;32m"   # Green
    ["WARN"]="\033[0;33m"   # Yellow
    ["ERROR"]="\033[0;31m"  # Red
    ["FATAL"]="\033[0;35m"  # Magenta
)
NC="\033[0m"

# Log function
log() {
    local level="$1"
    shift
    local message="$*"
    
    # Check log level
    if [[ ${LOG_LEVELS[$level]} -lt ${LOG_LEVELS[$LOG_LEVEL]} ]]; then
        return
    fi
    
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    local log_line="[$timestamp] [$level] $message"
    
    # Write to file
    echo "$log_line" >> "$LOG_FILE"
    
    # Write to terminal with color
    if [[ -t 1 ]]; then
        echo -e "${LOG_COLORS[$level]}$log_line${NC}" >&2
    fi
    
    # Special handling for FATAL
    if [[ "$level" == "FATAL" ]]; then
        exit 1
    fi
}

# Rotate logs
rotate_logs() {
    if [[ -f "$LOG_FILE" ]] && [[ $(stat -f%z "$LOG_FILE" 2>/dev/null || stat -c%s "$LOG_FILE") -gt $LOG_MAX_SIZE ]]; then
        for i in $(seq $((LOG_MAX_FILES-1)) -1 1); do
            [[ -f "${LOG_FILE}.$i" ]] && mv "${LOG_FILE}.$i" "${LOG_FILE}.$((i+1))"
        done
        mv "$LOG_FILE" "${LOG_FILE}.1"
    fi
}

# Convenience functions
debug() { log "DEBUG" "$*"; }
info() { log "INFO" "$*"; }
warn() { log "WARN" "$*"; }
error() { log "ERROR" "$*"; }
fatal() { log "FATAL" "$*"; }

# Usage
rotate_logs
info "Starting script..."
debug "Debug info: $variable"
warn "Warning: something unexpected"
error "Error occurred but continuing"
fatal "Fatal error, exiting"
```

**Q5: Implement connection pooling simulation for Bash.**

```bash
#!/bin/bash
# Simulated connection pooling for Bash

POOL_SIZE=5
POOL_DIR="/tmp/conn_pool_$$"
POOL_TIMEOUT=30

# Initialize pool
init_pool() {
    mkdir -p "$POOL_DIR"
    
    for i in $(seq 1 $POOL_SIZE); do
        # Create connection files (simulate connections)
        touch "$POOL_DIR/conn_$i"
        echo "available" > "$POOL_DIR/conn_$i"
    done
    
    echo "Pool initialized with $POOL_SIZE connections"
}

# Acquire connection
acquire_conn() {
    local timeout=${1:-$POOL_TIMEOUT}
    local waited=0
    
    while [[ $waited -lt $timeout ]]; do
        for i in $(seq 1 $POOL_SIZE); do
            local conn_file="$POOL_DIR/conn_$i"
            
            # Try to acquire lock atomically
            if (set -o noclobber; echo "in_use_$$" > "$conn_file" 2>/dev/null); then
                echo $i  # Return connection ID
                return 0
            fi
        done
        
        sleep 1
        ((waited++))
    done
    
    echo "Timeout waiting for connection" >&2
    return 1
}

# Execute with connection
exec_with_conn() {
    local conn_id=$1
    shift
    local cmd="$@"
    
    # Simulate using connection
    echo "Executing on connection $conn_id: $cmd"
    eval "$cmd"
}

# Release connection
release_conn() {
    local conn_id=$1
    echo "available" > "$POOL_DIR/conn_$conn_id"
}

# Cleanup pool
cleanup_pool() {
    rm -rf "$POOL_DIR"
}
trap cleanup_pool EXIT

# Example usage
init_pool

# Acquire, use, release
conn=$(acquire_conn)
exec_with_conn "$conn" "curl -s http://example.com"
release_conn "$conn"

# Cleanup handled by trap
```

**Q6: How do you implement retry logic with exponential backoff?**

```bash
#!/bin/bash
# Retry with exponential backoff

# Retry function
retry() {
    local max_attempts=$1
    local delay=$2
    local max_delay=$3
    shift 3
    local cmd="$@"
    
    local attempt=1
    local current_delay=$delay
    
    while [[ $attempt -le $max_attempts ]]; do
        echo "Attempt $attempt of $max_attempts: $cmd"
        
        if eval "$cmd"; then
            return 0
        fi
        
        if [[ $attempt -eq $max_attempts ]]; then
            echo "All attempts failed" >&2
            return 1
        fi
        
        echo "Failed. Retrying in ${current_delay}s..."
        sleep $current_delay
        
        # Exponential backoff with jitter
        current_delay=$((current_delay * 2))
        if [[ $current_delay -gt $max_delay ]]; then
            current_delay=$max_delay
        fi
        
        # Add jitter (±25%)
        local jitter=$((current_delay / 4))
        current_delay=$((current_delay + (RANDOM % (jitter * 2)) - jitter))
        
        ((attempt++))
    done
}

# Wrapper for common use cases
retry_http() {
    local url="$1"
    retry 5 1 30 "curl -sf '$url' > /dev/null"
}

retry_ssh() {
    local host="$1"
    shift
    local cmd="$@"
    retry 3 2 60 "ssh -o ConnectTimeout=10 '$host' '$cmd'"
}

# Example usage
retry 3 1 10 ping -c 1 google.com
retry_http "https://api.example.com/health"
```

**Q7: Create a modular script architecture.**

```bash
#!/bin/bash
# Modular script architecture

SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
LIB_DIR="$SCRIPT_DIR/lib"
MODULES_DIR="$SCRIPT_DIR/modules"

# Source library files
source_lib() {
    for lib in "$LIB_DIR"/*.sh; do
        [[ -f "$lib" ]] && source "$lib"
    done
}

# Load modules
load_module() {
    local module="$1"
    local module_file="$MODULES_DIR/${module}.sh"
    
    if [[ -f "$module_file" ]]; then
        source "$module_file"
        return 0
    else
        echo "Module not found: $module" >&2
        return 1
    fi
}

# Module registry
declare -A MODULES

register_module() {
    local name="$1"
    local description="$2"
    MODULES[$name]="$description"
}

list_modules() {
    echo "Available modules:"
    for name in "${!MODULES[@]}"; do
        printf "  %-15s %s\n" "$name" "${MODULES[$name]}"
    done
}

# Plugin system
run_hook() {
    local hook="$1"
    shift
    
    for plugin in "$PLUGINS_DIR"/${hook}_*.sh; do
        [[ -f "$plugin" ]] && source "$plugin" "$@"
    done
}

# Initialize
source_lib
load_module "logging"
load_module "database"
load_module "api"

# Main
run_hook "pre_main"
main "$@"
run_hook "post_main"
```

**Q8: Implement parallel execution with job control.**

```bash
#!/bin/bash
# Parallel execution with fine-grained control

MAX_PARALLEL=4
declare -a PIDS
declare -A JOBS

# Run job in background
run_job() {
    local job_name="$1"
    shift
    local cmd="$@"
    
    # Wait if at max parallel
    while [[ ${#PIDS[@]} -ge $MAX_PARALLEL ]]; do
        wait_any
    done
    
    # Run in background
    (
        echo "[$job_name] Starting..."
        eval "$cmd"
        local status=$?
        echo "[$job_name] Done (status: $status)"
        exit $status
    ) &
    
    local pid=$!
    PIDS+=($pid)
    JOBS[$pid]=$job_name
    echo "Started job '$job_name' (PID: $pid)"
}

# Wait for any job to complete
wait_any() {
    for pid in "${PIDS[@]}"; do
        if ! kill -0 $pid 2>/dev/null; then
            wait $pid
            local status=$?
            echo "Job '${JOBS[$pid]}' completed with status $status"
            unset 'JOBS[$pid]'
            
            # Remove from PIDS array
            PIDS=("${PIDS[@]/$pid}")
            return $status
        fi
    done
    
    # All still running, wait for one
    wait -n 2>/dev/null || wait
}

# Wait for all jobs
wait_all() {
    for pid in "${PIDS[@]}"; do
        wait $pid
        local status=$?
        echo "Job '${JOBS[$pid]}' finished with status $status"
    done
    PIDS=()
    JOBS=()
}

# Kill all jobs
kill_all() {
    for pid in "${PIDS[@]}"; do
        kill $pid 2>/dev/null
    done
}

# Usage
run_job "task1" sleep 3
run_job "task2" sleep 2
run_job "task3" sleep 4
run_job "task4" sleep 1
run_job "task5" sleep 2

wait_all
echo "All jobs completed!"
```

**Q9: How do you create a state machine in Bash?**

```bash
#!/bin/bash
# State machine implementation

declare -A STATES
declare -A TRANSITIONS
CURRENT_STATE="initial"

# Define states
define_state() {
    local name="$1"
    local handler="$2"
    STATES[$name]="$handler"
}

# Define transitions
define_transition() {
    local from="$1"
    local event="$2"
    local to="$3"
    TRANSITIONS["$from:$event"]="$to"
}

# Process event
process_event() {
    local event="$1"
    local transition_key="$CURRENT_STATE:$event"
    
    if [[ -v TRANSITIONS[$transition_key] ]]; then
        local next_state="${TRANSITIONS[$transition_key]}"
        echo "Transition: $CURRENT_STATE --[$event]--> $next_state"
        
        # Execute exit handler
        if [[ -v STATES[$CURRENT_STATE] ]]; then
            ${STATES[$CURRENT_STATE]} "exit"
        fi
        
        # Change state
        CURRENT_STATE="$next_state"
        
        # Execute enter handler
        if [[ -v STATES[$CURRENT_STATE] ]]; then
            ${STATES[$CURRENT_STATE]} "enter"
        fi
    else
        echo "Invalid event '$event' in state '$CURRENT_STATE'"
    fi
}

# Define state handlers
state_idle() {
    local action="$1"
    case "$action" in
        enter) echo "Entering IDLE state" ;;
        exit) echo "Leaving IDLE state" ;;
    esac
}

state_running() {
    local action="$1"
    case "$action" in
        enter) echo "Starting process..." ;;
        exit) echo "Stopping process..." ;;
    esac
}

state_completed() {
    local action="$1"
    case "$action" in
        enter) echo "Process completed!" ;;
        exit) ;;
    esac
}

# Setup state machine
define_state "idle" state_idle
define_state "running" state_running
define_state "completed" state_completed

define_transition "idle" "start" "running"
define_transition "running" "complete" "completed"
define_transition "running" "error" "idle"
define_transition "completed" "reset" "idle"

# Run state machine
${STATES[$CURRENT_STATE]} "enter"
process_event "start"
process_event "complete"
process_event "reset"
```

**Q10: Create a self-updating script.**

```bash
#!/bin/bash
# Self-updating script

SCRIPT_NAME="$(basename "$0")"
SCRIPT_URL="https://raw.githubusercontent.com/user/repo/main/script.sh"
VERSION="1.0.0"
SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
SCRIPT_PATH="$SCRIPT_DIR/$SCRIPT_NAME"

# Check for updates
check_update() {
    local force=${1:-false}
    
    # Get remote version
    local remote_version
    remote_version=$(curl -sf "$SCRIPT_URL" | grep '^VERSION=' | cut -d'"' -f2)
    
    if [[ -z "$remote_version" ]]; then
        echo "Failed to check for updates" >&2
        return 1
    fi
    
    if [[ "$remote_version" != "$VERSION" ]] || [[ "$force" == "true" ]]; then
        echo "Update available: $VERSION -> $remote_version"
        return 0
    else
        echo "Already up to date (v$VERSION)"
        return 1
    fi
}

# Perform update
do_update() {
    echo "Updating $SCRIPT_NAME..."
    
    # Backup current script
    cp "$SCRIPT_PATH" "${SCRIPT_PATH}.bak"
    
    # Download new version
    if curl -sf "$SCRIPT_URL" -o "${SCRIPT_PATH}.new"; then
        # Make executable
        chmod +x "${SCRIPT_PATH}.new"
        
        # Replace old version
        mv "${SCRIPT_PATH}.new" "$SCRIPT_PATH"
        
        echo "Update complete! Reloading..."
        exec "$SCRIPT_PATH" "${ARGS[@]}"
    else
        echo "Update failed! Restoring backup..." >&2
        mv "${SCRIPT_PATH}.bak" "$SCRIPT_PATH"
        return 1
    fi
}

# Self-update check (run in background)
auto_update_check() {
    (
        sleep 5  # Don't block startup
        if check_update; then
            # Notify user
            echo "Update available! Run: $SCRIPT_NAME --update"
        fi
    ) &
}

# Parse arguments
ARGS=("$@")
while [[ $# -gt 0 ]]; do
    case "$1" in
        --update)
            check_update true && do_update
            exit $?
            ;;
        --check-update)
            check_update
            exit $?
            ;;
        --version)
            echo "$SCRIPT_NAME v$VERSION"
            exit 0
            ;;
    esac
    shift
done

# Main
auto_update_check
echo "Running $SCRIPT_NAME v$VERSION..."
```

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Automated Deployment Pipeline

```
┌─────────────────────────────────────────────────────────────────────────┐
│                   SCENARIO: CI/CD Deployment Script                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Task: Create deployment script that:                                   │
│  • Runs tests before deployment                                         │
│  • Handles rollback on failure                                          │
│  • Sends notifications                                                   │
│  • Maintains deployment history                                          │
│                                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  #!/bin/bash                                                            │
│  set -euo pipefail                                                      │
│                                                                          │
│  APP_NAME="myapp"                                                       │
│  DEPLOY_DIR="/var/www/$APP_NAME"                                        │
│  BACKUP_DIR="/var/backups/$APP_NAME"                                    │
│  REPO_URL="git@github.com:user/repo.git"                                │
│                                                                          │
│  # Logging                                                              │
│  log() { echo "[$(date '+%Y-%m-%d %H:%M:%S')] $*"; }                   │
│  notify() { termux-notification --title "Deploy" --content "$1"; }      │
│                                                                          │
│  # Pre-deploy checks                                                    │
│  pre_deploy() {                                                          │
│      log "Running pre-deploy checks..."                                 │
│      command -v git >/dev/null || { log "Git not found"; return 1; }   │
│      [[ -d "$DEPLOY_DIR" ]] || mkdir -p "$DEPLOY_DIR"                  │
│  }                                                                       │
│                                                                          │
│  # Run tests                                                             │
│  run_tests() {                                                           │
│      log "Running tests..."                                             │
│      cd "$DEPLOY_DIR"                                                   │
│          npm test || { log "Tests failed!"; return 1; }                │
│      )                                                                   │
│  }                                                                       │
│                                                                          │
│  # Backup current version                                               │
│  backup() {                                                              │
│      local timestamp=$(date +%Y%m%d_%H%M%S)                             │
│      log "Creating backup..."                                           │
│      tar -czf "$BACKUP_DIR/backup_$timestamp.tar.gz" -C "$DEPLOY_DIR" .│
│  }                                                                       │
│                                                                          │
│  # Deploy                                                                │
│  deploy() {                                                              │
│      log "Deploying..."                                                 │
│      git clone "$REPO_URL" "$DEPLOY_DIR/new"                            │
│      mv "$DEPLOY_DIR/current" "$DEPLOY_DIR/old" 2>/dev/null || true    │
│      mv "$DEPLOY_DIR/new" "$DEPLOY_DIR/current"                        │
│      rm -rf "$DEPLOY_DIR/old"                                           │
│  }                                                                       │
│                                                                          │
│  # Rollback                                                              │
│  rollback() {                                                            │
│      log "Rolling back..."                                              │
│      rm -rf "$DEPLOY_DIR/current"                                       │
│      mv "$DEPLOY_DIR/old" "$DEPLOY_DIR/current"                         │
│  }                                                                       │
│                                                                          │
│  # Main                                                                  │
│  main() {                                                                │
│      pre_deploy && backup && run_tests && deploy                        │
│      notify "Deployment successful!"                                    │
│  }                                                                       │
│                                                                          │
│  trap 'rollback; notify "Deployment failed!"' ERR                       │
│  main                                                                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Scenario 2: Security Hardening Script

```
┌─────────────────────────────────────────────────────────────────────────┐
│                   SCENARIO: System Security Audit                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Task: Create security audit script for Termux:                         │
│  • Check for vulnerable packages                                        │
│  • Audit file permissions                                               │
│  • Check SSH configuration                                              │
│  • Generate security report                                             │
│                                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  #!/bin/bash                                                            │
│  # Security audit script                                                │
│                                                                          │
│  REPORT="$HOME/security_audit_$(date +%Y%m%d).txt"                      │
│  ISSUES=0                                                               │
│                                                                          │
│  check() {                                                              │
│      local test_name="$1"                                               │
│      local result="$2"                                                  │
│      if [[ "$result" == "FAIL" ]]; then                                 │
│          echo "[!] $test_name: FAIL" | tee -a "$REPORT"                │
│          ((ISSUES++))                                                   │
│      else                                                                │
│          echo "[✓] $test_name: PASS" | tee -a "$REPORT"                │
│      fi                                                                  │
│  }                                                                       │
│                                                                          │
│  echo "=== Security Audit Report ===" > "$REPORT"                       │
│  echo "Date: $(date)" >> "$REPORT"                                      │
│                                                                          │
│  # Check package vulnerabilities                                        │
│  audit_packages() {                                                      │
│      local outdated=$(pkg list-upgradable 2>/dev/null | wc -l)          │
│      check "Outdated packages" $([[ $outdated -eq 0 ]] && echo PASS)    │
│  }                                                                       │
│                                                                          │
│  # Check file permissions                                               │
│  audit_permissions() {                                                  │
│      local world_writable=$(find ~ -perm -002 -type f 2>/dev/null | wc -l)│
│      check "World-writable files" $([[ $world_writable -eq 0 ]] && echo PASS)│
│  }                                                                       │
│                                                                          │
│  # Check SSH config                                                      │
│  audit_ssh() {                                                           │
│      if [[ -f ~/.ssh/config ]]; then                                    │
│          grep -q "PasswordAuthentication no" ~/.ssh/config 2>/dev/null  │
│          check "SSH password auth disabled" $?                          │
│      fi                                                                  │
│  }                                                                       │
│                                                                          │
│  # Check sensitive files                                                 │
│  audit_sensitive() {                                                    │
│      local exposed=$(find ~ -name "*.key" -o -name "*.pem" \            │
│          -perm -004 2>/dev/null | wc -l)                                │
│      check "Exposed private keys" $([[ $exposed -eq 0 ]] && echo PASS)  │
│  }                                                                       │
│                                                                          │
│  # Run all audits                                                        │
│  audit_packages                                                         │
│  audit_permissions                                                      │
│  audit_ssh                                                              │
│  audit_sensitive                                                        │
│                                                                          │
│  echo "" >> "$REPORT"                                                   │
│  echo "Total issues: $ISSUES" >> "$REPORT"                              │
│  echo "Report saved to: $REPORT"                                        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Scenario 3: Log Aggregation System

```
┌─────────────────────────────────────────────────────────────────────────┐
│                   SCENARIO: Centralized Log Management                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Task: Create log aggregation system:                                   │
│  • Collect logs from multiple sources                                   │
│  • Parse and filter entries                                             │
│  • Generate summary reports                                              │
│  • Archive old logs                                                      │
│                                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  #!/bin/bash                                                            │
│  # Log aggregation system                                               │
│                                                                          │
│  LOG_DIR="$HOME/logs"                                                   │
│  ARCHIVE_DIR="$HOME/log_archive"                                        │
│  SOURCES=("$HOME/.bash_history" "/var/log/syslog")                      │
│                                                                          │
│  # Collect logs                                                          │
│  collect_logs() {                                                        │
│      mkdir -p "$LOG_DIR"                                                │
│      for source in "${SOURCES[@]}"; do                                  │
│          [[ -f "$source" ]] && cp "$source" "$LOG_DIR/$(basename $source)"│
│      done                                                                │
│  }                                                                       │
│                                                                          │
│  # Parse logs                                                            │
│  parse_logs() {                                                          │
│      local output="$LOG_DIR/parsed_$(date +%Y%m%d).log"                 │
│      for log in "$LOG_DIR"/*; do                                        │
│          # Extract errors and warnings                                  │
│          grep -iE "(error|warning|fail|critical)" "$log" >> "$output"   │
│      done                                                                │
│  }                                                                       │
│                                                                          │
│  # Generate report                                                       │
│  generate_report() {                                                     │
│      local report="$LOG_DIR/report_$(date +%Y%m%d).txt"                 │
│      echo "=== Log Summary $(date) ===" > "$report"                     │
│      echo "Total errors: $(grep -c 'error' "$LOG_DIR"/*.log 2>/dev/null)" >> "$report"│
│      echo "Total warnings: $(grep -c 'warning' "$LOG_DIR"/*.log 2>/dev/null)" >> "$report"│
│  }                                                                       │
│                                                                          │
│  # Archive old logs                                                      │
│  archive_logs() {                                                        │
│      mkdir -p "$ARCHIVE_DIR"                                            │
│      find "$LOG_DIR" -name "*.log" -mtime +7 -exec gzip {} \;           │
│      mv "$LOG_DIR"/*.gz "$ARCHIVE_DIR/" 2>/dev/null || true            │
│  }                                                                       │
│                                                                          │
│  # Main                                                                  │
│  collect_logs                                                            │
│  parse_logs                                                              │
│  generate_report                                                        │
│  archive_logs                                                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Scenario 4: Resource Monitoring Dashboard

```
┌─────────────────────────────────────────────────────────────────────────┐
│                   SCENARIO: System Resource Monitor                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Task: Create resource monitoring script:                               │
│  • Monitor CPU, memory, disk usage                                      │
│  • Alert on threshold breach                                            │
│  • Log historical data                                                   │
│  • Generate usage graphs (ASCII)                                         │
│                                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  #!/bin/bash                                                            │
│  # Resource monitoring dashboard                                        │
│                                                                          │
│  LOG_FILE="$HOME/resource_monitor.log"                                  │
│  ALERT_CPU=80                                                           │
│  ALERT_MEM=90                                                           │
│  ALERT_DISK=85                                                          │
│                                                                          │
│  # Get CPU usage                                                         │
│  get_cpu() {                                                             │
│      top -bn1 | grep "CPU:" | awk '{print $2}' | cut -d'%' -f1          │
│  }                                                                       │
│                                                                          │
│  # Get memory usage                                                      │
│  get_mem() {                                                             │
│      free | grep Mem | awk '{printf "%.0f", $3/$2 * 100}'               │
│  }                                                                       │
│                                                                          │
│  # Get disk usage                                                        │
│  get_disk() {                                                            │
│      df -h / | tail -1 | awk '{print $5}' | tr -d '%'                   │
│  }                                                                       │
│                                                                          │
│  # ASCII bar chart                                                       │
│  draw_bar() {                                                            │
│      local value=$1                                                      │
│      local width=20                                                      │
│      local filled=$((value * width / 100))                              │
│      local empty=$((width - filled))                                    │
│      printf "[%s%s] %d%%" "$(printf '#%.0s' $(seq 1 $filled))" \        │
│          "$(printf ' %.0s' $(seq 1 $empty))" "$value"                    │
│  }                                                                       │
│                                                                          │
│  # Alert function                                                        │
│  alert() {                                                               │
│      local resource="$1"                                                │
│      local value="$2"                                                   │
│      echo "[ALERT] $resource usage: $value%"                            │
│      termux-notification --title "Resource Alert" \                     │
│          --content "$resource at $value%"                               │
│  }                                                                       │
│                                                                          │
│  # Monitor loop                                                          │
│  monitor() {                                                             │
│      while true; do                                                      │
│          clear                                                           │
│          echo "=== System Resources ==="                                │
│          echo "Time: $(date '+%H:%M:%S')"                               │
│          echo ""                                                         │
│                                                                          │
│          cpu=$(get_cpu)                                                 │
│          mem=$(get_mem)                                                 │
│          disk=$(get_disk)                                               │
│                                                                          │
│          printf "CPU:  "; draw_bar $cpu; echo                           │
│          printf "MEM:  "; draw_bar $mem; echo                           │
│          printf "DISK: "; draw_bar $disk; echo                          │
│                                                                          │
│          # Check thresholds                                              │
│          [[ $cpu -gt $ALERT_CPU ]] && alert "CPU" $cpu                  │
│          [[ $mem -gt $ALERT_MEM ]] && alert "Memory" $mem               │
│          [[ $disk -gt $ALERT_DISK ]] && alert "Disk" $disk              │
│                                                                          │
│          # Log data                                                      │
│          echo "$(date),$cpu,$mem,$disk" >> "$LOG_FILE"                  │
│                                                                          │
│          sleep 5                                                        │
│      done                                                                │
│  }                                                                       │
│                                                                          │
│  monitor                                                                 │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Scenario 5: Automated Testing Framework

```
┌─────────────────────────────────────────────────────────────────────────┐
│                   SCENARIO: Bash Testing Framework                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Task: Create testing framework for Bash scripts:                       │
│  • Define test cases                                                    │
│  • Run assertions                                                        │
│  • Generate test reports                                                 │
│  • Track test coverage                                                   │
│                                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  #!/bin/bash                                                            │
│  # Simple Bash testing framework                                        │
│                                                                          │
│  TESTS_RUN=0                                                            │
│  TESTS_PASSED=0                                                         │
│  TESTS_FAILED=0                                                         │
│  CURRENT_TEST=""                                                        │
│                                                                          │
│  # Colors                                                               │
│  RED='\033[0;31m'                                                       │
│  GREEN='\033[0;32m'                                                     │
│  NC='\033[0m'                                                           │
│                                                                          │
│  # Test definition                                                       │
│  test_begin() {                                                          │
│      CURRENT_TEST="$1"                                                  │
│      ((TESTS_RUN++))                                                    │
│      echo -n "Testing: $CURRENT_TEST ... "                              │
│  }                                                                       │
│                                                                          │
│  test_pass() {                                                           │
│      echo -e "${GREEN}PASS${NC}"                                        │
│      ((TESTS_PASSED++))                                                 │
│  }                                                                       │
│                                                                          │
│  test_fail() {                                                           │
│      echo -e "${RED}FAIL${NC}"                                          │
│      ((TESTS_FAILED++))                                                 │
│      echo "  Error: $1"                                                 │
│  }                                                                       │
│                                                                          │
│  # Assertions                                                            │
│  assert_equals() {                                                       │
│      local expected="$1"                                                │
│      local actual="$2"                                                  │
│      if [[ "$expected" == "$actual" ]]; then                            │
│          test_pass                                                      │
│      else                                                                │
│          test_fail "Expected '$expected' but got '$actual'"             │
│      fi                                                                  │
│  }                                                                       │
│                                                                          │
│  assert_true() {                                                         │
│      if $@; then                                                         │
│          test_pass                                                      │
│      else                                                                │
│          test_fail "Expected true but was false"                        │
│      fi                                                                  │
│  }                                                                       │
│                                                                          │
│  assert_file_exists() {                                                 │
│      if [[ -f "$1" ]]; then                                             │
│          test_pass                                                      │
│      else                                                                │
│          test_fail "File does not exist: $1"                            │
│      fi                                                                  │
│  }                                                                       │
│                                                                          │
│  # Test summary                                                          │
│  test_summary() {                                                        │
│      echo ""                                                             │
│      echo "=== Test Summary ==="                                        │
│      echo "Tests run: $TESTS_RUN"                                       │
│      echo "Passed: $TESTS_PASSED"                                       │
│      echo "Failed: $TESTS_FAILED"                                       │
│      [[ $TESTS_FAILED -eq 0 ]]                                          │
│  }                                                                       │
│                                                                          │
│  # Example tests                                                         │
│  test_begin "Math operations"                                           │
│  result=$((5 + 5))                                                      │
│  assert_equals 10 $result                                               │
│                                                                          │
│  test_begin "String length"                                             │
│  str="Hello"                                                            │
│  assert_equals 5 ${#str}                                                │
│                                                                          │
│  test_summary                                                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: Signal Handling Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SIGNAL HANDLING FLOW                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌──────────────────┐                                                  │
│   │   User/System    │                                                  │
│   │   Sends Signal   │                                                  │
│   └────────┬─────────┘                                                  │
│            │                                                             │
│            ▼                                                             │
│   ┌──────────────────────────────────────────────────┐                  │
│   │              SIGNAL TRAP CHECK                    │                  │
│   │   Is there a trap registered for this signal?    │                  │
│   └────────────────────────┬─────────────────────────┘                  │
│                            │                                             │
│              ┌─────────────┴─────────────┐                              │
│              │                           │                               │
│        ┌─────▼─────┐               ┌─────▼─────┐                        │
│        │   YES     │               │    NO     │                        │
│        │           │               │           │                        │
│        │ Execute   │               │ Default   │                        │
│        │ Trap      │               │ Action    │                        │
│        │ Handler   │               │           │                        │
│        └─────┬─────┘               └─────┬─────┘                        │
│              │                           │                               │
│              └─────────────┬─────────────┘                              │
│                            │                                             │
│                            ▼                                             │
│   ┌──────────────────────────────────────────────────┐                  │
│   │              SIGNAL HANDLER                       │                  │
│   │                                                  │                  │
│   │   cleanup() {                                    │                  │
│   │       echo "Cleaning up..."                     │                  │
│   │       rm -f "$TEMP_FILE"                        │                  │
│   │       kill_background_jobs                      │                  │
│   │       close_connections                         │                  │
│   │   }                                              │                  │
│   │                                                  │                  │
│   │   trap cleanup EXIT INT TERM                    │                  │
│   └──────────────────────────────────────────────────┘                  │
│                                                                          │
│   COMMON SIGNALS:                                                       │
│   ┌─────────┬─────────────────────────────────────┐                    │
│   │ Signal  │ Use Case                            │                    │
│   ├─────────┼─────────────────────────────────────┤                    │
│   │ EXIT    │ Always runs on script termination   │                    │
│   │ INT     │ Ctrl+C - User interrupt             │                    │
│   │ TERM    │ Normal termination request          │                    │
│   │ HUP     │ Hangup - Terminal closed            │                    │
│   │ ERR     │ Command error (with set -e)         │                    │
│   │ DEBUG   │ Runs before every command           │                    │
│   └─────────┴─────────────────────────────────────┘                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: Process Substitution Mechanism

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PROCESS SUBSTITUTION MECHANISM                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   INPUT SUBSTITUTION <()                                                 │
│   ───────────────────────                                               │
│                                                                          │
│   diff <(sort file1) <(sort file2)                                      │
│                                                                          │
│   ┌─────────┐      ┌─────────┐      ┌─────────┐                         │
│   │ sort    │      │ sort    │      │  diff   │                         │
│   │ file1   │──────│ file2   │──────│ command │                         │
│   └────┬────┘      └────┬────┘      └────┬────┘                         │
│        │                │                │                               │
│        ▼                ▼                ▼                               │
│   ┌─────────┐      ┌─────────┐      ┌─────────┐                         │
│   │ /dev/fd │      │ /dev/fd │      │ Reads   │                         │
│   │   /63   │      │   /62   │      │ both    │                         │
│   └─────────┘      └─────────┘      └─────────┘                         │
│                                                                          │
│   Bash creates temporary file descriptors                               │
│   that behave like files containing command output                      │
│                                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   OUTPUT SUBSTITUTION >()                                                │
│   ────────────────────────                                              │
│                                                                          │
│   tee >(process1) >(process2) > output.txt                              │
│                                                                          │
│   ┌─────────────────────────────────────────────────┐                  │
│   │                    tee command                   │                  │
│   └─────────────────────┬───────────────────────────┘                  │
│                         │                                                │
│         ┌───────────────┼───────────────┬───────────────┐              │
│         │               │               │               │               │
│         ▼               ▼               ▼               ▼               │
│   ┌─────────┐     ┌─────────┐     ┌─────────┐     ┌─────────┐          │
│   │ process1│     │ process2│     │ output  │     │ stdout  │          │
│   │         │     │         │     │ .txt    │     │         │          │
│   └─────────┘     └─────────┘     └─────────┘     └─────────┘          │
│                                                                          │
│   Data flows to multiple destinations simultaneously                    │
│                                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   PRACTICAL EXAMPLES:                                                   │
│                                                                          │
│   # Compare directory contents                                          │
│   diff <(ls dir1 | sort) <(ls dir2 | sort)                              │
│                                                                          │
│   # Process in loop without subshell issues                             │
│   while read line; do                                                   │
│       ((count++))                                                       │
│   done < <(grep "pattern" file.txt)                                     │
│                                                                          │
│   # Multiple output streams                                             │
│   command | tee >(grep error > errors.txt) \                           │
│                  >(grep warn > warnings.txt) > all.txt                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: Error Handling Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ERROR HANDLING ARCHITECTURE                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    SCRIPT START                                  │   │
│   └──────────────────────────┬──────────────────────────────────────┘   │
│                              │                                           │
│                              ▼                                           │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    STRICT MODE SETUP                             │   │
│   │                                                                  │   │
│   │   set -e          # Exit on error                               │   │
│   │   set -u          # Error on undefined variable                 │   │
│   │   set -o pipefail # Pipeline error propagation                  │   │
│   │   set -x          # Debug mode (optional)                       │   │
│   └──────────────────────────┬──────────────────────────────────────┘   │
│                              │                                           │
│                              ▼                                           │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    TRAP SETUP                                    │   │
│   │                                                                  │   │
│   │   trap cleanup EXIT        # Always cleanup                     │   │
│   │   trap 'on_error $LINENO' ERR    # Error handler                │   │
│   │   trap on_interrupt INT    # Ctrl+C handler                     │   │
│   │   trap on_terminate TERM   # Kill handler                       │   │
│   └──────────────────────────┬──────────────────────────────────────┘   │
│                              │                                           │
│                              ▼                                           │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    MAIN EXECUTION                                │   │
│   │                                                                  │   │
│   │   command1 && command2 || fallback                              │   │
│   │   if ! command; then handle_error; fi                           │   │
│   │                                                                  │   │
│   └──────────────────────────┬──────────────────────────────────────┘   │
│                              │                                           │
│            ┌─────────────────┼─────────────────┐                        │
│            │                 │                 │                         │
│      ┌─────▼─────┐     ┌─────▼─────┐     ┌─────▼─────┐                  │
│      │  SUCCESS  │     │   ERROR   │     │ INTERRUPT │                  │
│      │           │     │           │     │           │                  │
│      │ Continue  │     │ set -e    │     │ Ctrl+C    │                  │
│      │           │     │ triggers  │     │ triggers  │                  │
│      └─────┬─────┘     └─────┬─────┘     └─────┬─────┘                  │
│            │                 │                 │                         │
│            └─────────────────┼─────────────────┘                        │
│                              │                                           │
│                              ▼                                           │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    CLEANUP & EXIT                                │   │
│   │                                                                  │   │
│   │   cleanup() {                                                   │   │
│   │       rm -f "$TEMP_FILES"                                       │   │
│   │       kill "$BG_PIDS"                                           │   │
│   │       close_connections                                         │   │
│   │       write_log                                                 │   │
│   │   }                                                              │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Title | Relevance |
|---------|-------|-----------|
| Ch13 | Bash Scripting Basics | Foundation for this chapter |
| Ch15 | Git Version Control | Script version control |
| Ch17 | Termux API | Bash + Android integration |
| Ch21 | Cron Jobs | Scheduling bash scripts |
| Ch25 | Process Management | Background processes |
| Ch27 | Regular Expressions | Pattern matching in scripts |
| Ch30 | DevOps Tools | Automation pipelines |

---

## 🏆 BONUS ADVANCED CONTENT

### Technique 1: Advanced Debugging Framework

```bash
#!/bin/bash
# Advanced debugging framework

DEBUG=${DEBUG:-false}
DEBUG_LOG="/tmp/debug_$$.log"

# Debug function
_debug() {
    [[ "$DEBUG" != "true" ]] && return
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S.%3N')
    echo "[$timestamp] $*" >> "$DEBUG_LOG"
}

# Trace function calls
_trace() {
    _debug "TRACE: ${FUNCNAME[1]}() called from ${BASH_SOURCE[2]}:${BASH_LINENO[1]}"
}

# Variable watch
_watch() {
    local var_name="$1"
    _debug "WATCH: $var_name = '${!var_name}'"
}

# Function entry/exit logging
log_function() {
    if [[ "$1" == "enter" ]]; then
        _debug "ENTER: ${FUNCNAME[1]}() args: ${*:2}"
    else
        _debug "EXIT: ${FUNCNAME[1]}() result: $?"
    fi
}

# Example usage with decorator
with_logging() {
    local func="$1"
    shift
    log_function "enter" "$@"
    "$func" "$@"
    local result=$?
    log_function "exit"
    return $result
}

# Stack trace on error
stack_trace() {
    local frame=0
    echo "Stack trace:"
    while caller $frame; do
        ((frame++))
    done | awk '{print "  at " $3 ":" $1 " in " $2}'
}

trap 'stack_trace' ERR
```

### Technique 2: Bash Object-Oriented Patterns

```bash
#!/bin/bash
# Object-oriented patterns in Bash

# Class definition using associative arrays
class_User() {
    # Constructor
    User() {
        local instance="$1"
        local name="${2:-Anonymous}"
        local email="${3:-}"
        
        # Instance variables
        declare -gA ${instance}
        eval "${instance}[name]='$name'"
        eval "${instance}[email]='$email'"
        eval "${instance}[created]='$(date)'"
    }
    
    # Method: greet
    User.greet() {
        local instance="$1"
        local name=$(eval echo "\${${instance}[name]}")
        echo "Hello, I'm $name!"
    }
    
    # Method: set_email
    User.set_email() {
        local instance="$1"
        local email="$2"
        eval "${instance}[email]='$email'"
    }
    
    # Method: get_info
    User.get_info() {
        local instance="$1"
        eval "echo 'Name: \${${instance}[name]}, Email: \${${instance}[email]}'"
    }
}

# Create instances
class_User
User user1 "T3rmuxk1ng" "admin@termux.dev"
User user2 "Guest"

# Call methods
User.greet user1
User.set_email user1 "new@email.com"
User.get_info user1
User.greet user2
```

### Technique 3: Build System Pattern

```bash
#!/bin/bash
# Build system pattern for Bash projects

BUILD_DIR="${BUILD_DIR:-./build}"
SOURCE_DIR="${SOURCE_DIR:-./src}"
CACHE_DIR="${CACHE_DIR:-./.cache}"

declare -A TASKS
declare -A DEPS
declare -A DONE

# Register task
task() {
    local name="$1"
    local deps="$2"
    local handler="$3"
    
    TASKS[$name]="$handler"
    DEPS[$name]="$deps"
}

# Run task with dependency resolution
run_task() {
    local task="$1"
    
    # Already done?
    [[ -v DONE[$task] ]] && return 0
    
    # Check dependencies
    for dep in ${DEPS[$task]}; do
        run_task "$dep" || return 1
    done
    
    # Run task
    echo "Running task: $task"
    ${TASKS[$task]}
    local result=$?
    
    # Mark done
    DONE[$task]=1
    return $result
}

# Define tasks
task "clean" "" "
    rm -rf '$BUILD_DIR' '$CACHE_DIR'
    echo 'Cleaned!'
"

task "setup" "clean" "
    mkdir -p '$BUILD_DIR' '$CACHE_DIR'
    echo 'Setup complete!'
"

task "compile" "setup" "
    for src in '$SOURCE_DIR'/*.sh; do
        cp \"\$src\" '$BUILD_DIR/'
    done
    echo 'Compiled!'
"

task "test" "compile" "
    cd '$BUILD_DIR'
    for test in test_*.sh; do
        bash \"\$test\" || exit 1
    done
    echo 'Tests passed!'
"

task "build" "test" "
    echo 'Build complete!'
"

# Run build
run_task "build"
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

- [ ] **Error Handling Mastery**
  - [ ] Understand set -e, set -u, set -o pipefail
  - [ ] Implement trap for cleanup
  - [ ] Handle ERR signal
  - [ ] Create custom error handlers

- [ ] **Signal Processing**
  - [ ] Know common signals (INT, TERM, HUP, EXIT)
  - [ ] Implement graceful shutdown
  - [ ] Handle user interrupts
  - [ ] Use signals for IPC

- [ ] **Regular Expressions**
  - [ ] Use =~ operator
  - [ ] Extract capture groups with BASH_REMATCH
  - [ ] Validate input with regex
  - [ ] Combine with grep/sed/awk

- [ ] **Process Substitution**
  - [ ] Understand <() input substitution
  - [ ] Use >() output substitution
  - [ ] Avoid subshell variable issues
  - [ ] Create efficient pipelines

- [ ] **Here Documents & Strings**
  - [ ] Multi-line text with here-docs
  - [ ] Quoted vs unquoted delimiters
  - [ ] Here strings for single-line input
  - [ ] Generate configs dynamically

- [ ] **Advanced Text Processing**
  - [ ] Master sed commands
  - [ ] Use awk for data extraction
  - [ ] Process CSV/JSON data
  - [ ] Build text processing pipelines

- [ ] **CLI Tool Development**
  - [ ] Use getopts for option parsing
  - [ ] Implement long options
  - [ ] Create help systems
  - [ ] Follow CLI conventions

- [ ] **Security Practices**
  - [ ] Validate all user input
  - [ ] Avoid injection vulnerabilities
  - [ ] Use secure temp files
  - [ ] Set proper permissions

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

**Q13: What is `BASH_REMATCH` used for?**
- A) Rematching patterns
- B) Storing regex capture groups
- C) Bash version info
- D) Remapping keys

<details>
<summary>Answer</summary>
**B) Storing regex capture groups** - After a regex match with `=~`, `BASH_REMATCH` array contains the matched groups.
</details>

---

**Q14: How do you create a named pipe?**
- A) `pipe name`
- B) `mkfifo name`
- C) `mkpipe name`
- D) `create pipe name`

<details>
<summary>Answer</summary>
**B) `mkfifo name`** - Creates a FIFO (named pipe) for inter-process communication.
</details>

---

**Q15: What does `coproc` do in Bash?**
- A) Copies processes
- B) Creates a coprocess
- C) Compiles scripts
- D) Coordinates processes

<details>
<summary>Answer</summary>
**B) Creates a coprocess** - `coproc` creates a coprocess that runs in the background with its own stdin/stdout pipes.
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
