import time
import os

def follow(file_path):
    try:
        with open(file_path, "r") as file:
            # Move to the end of file
            file.seek(0, os.SEEK_END)

            print(f"Monitoring {file_path}...\n")

            while True:
                line = file.readline()
                if not line:
                    time.sleep(0.5)
                    continue
                print(line, end="")

    except FileNotFoundError:
        print("File not found.")
    except KeyboardInterrupt:
        print("\nStopped monitoring.")

if __name__ == "__main__":
    path = input("Enter log file path: ").strip()
    follow(path)
