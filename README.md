# Simple-Log-Parser
Python script to parse logs and look for potential malicious activity such as failed login attempts. This is useful for SOC analysts or system administrators to detect signs of a brute-force attack or unauthorized access.
import re

def parse_log(file_path):
    # Define the pattern for failed login attempts
    pattern = r"Failed password for (.*) from (.*) port"

    # Open the log file
    with open(file_path, 'r') as log_file:
        for line in log_file:
            match = re.search(pattern, line)
            if match:
                user = match.group(1)
                ip = match.group(2)
                print(f"Failed login attempt by user: {user} from IP: {ip}")

# Main Program
if __name__ == "__main__":
    log_file_path = input("Enter log file path: ")
    parse_log(log_file_path)
