# Git-Green

This project automates the process of committing and pushing changes to a Git repository and includes a Bash script with a loading animation for running tasks like executing Node.js scripts. The functionality focuses on:

1. Appending data to a file using Node.js (`app.js`).
2. Automating Git workflows (add, commit, push).
3. Running a long-running process with a user-friendly loading animation in Bash (`bash.sh`).
4. Scheduling daily commits using a task scheduler.

## Files

### 1. `app.js`
- Uses Node.js to:
  - Append data to a file (`filename.txt`).
  - Execute Git commands (`git add`, `git commit`, `git push`) for automation.
- Features error handling for file operations and command execution.

### 2. `bash.sh`
- Bash script to:
  - Navigate to the directory containing the Node.js script.
  - Execute the `app.js` file using Node.js.
  - Display a loading animation while the process runs in the background.

## Requirements

### Node.js Dependencies
Ensure the following modules are installed in your project:
- `fs`
- `child_process`

Install them using:
```bash
npm install
```

### Bash Script
Make sure the `bash.sh` file has executable permissions. Run the following command:
```bash
chmod +x bash.sh
```

### Task Scheduler for Daily Commits

To schedule daily commits, follow these steps:

#### Windows
1. Open Task Scheduler and create a new task.
2. Set the trigger to run daily at your preferred time.
3. Set the action to run `bash.sh`. Example command:
   ```
   C:\path\to\bash.sh
   ```
4. Save the task.

#### Linux
1. Open the crontab file:
   ```bash
   crontab -e
   ```
2. Add an entry to schedule `bash.sh` daily. Example:
   ```
   0 9 * * * /path/to/bash.sh
   ```
   This runs the script every day at 9 AM.

#### MacOS
1. Use `launchd` to schedule the task.
2. Create a `.plist` file in `~/Library/LaunchAgents`.
3. Add the script execution details and load the `.plist` file using:
   ```bash
   launchctl load ~/Library/LaunchAgents/com.example.dailycommit.plist
   ```

## Usage

### Run the Bash Script
Execute the Bash script with:
```bash
./bash.sh
```
This will:
1. Navigate to the specified directory.
2. Run the Node.js script (`app.js`).
3. Display a loading animation until the script finishes execution.

### Auto-Commit and Push
The `app.js` script:
1. Stages all changes in the repository.
2. Commits the changes with a timestamped message.
3. Pushes the changes to the remote repository.

### Scheduled Daily Commits
Once the task is scheduled, the script will run automatically at the specified time every day, ensuring regular updates to the repository.

## Customization
- Modify the file path in `bash.sh` to point to your project directory.
- Customize the Git commit message logic in `app.js` if needed.

## Example Output

### Bash Script Output
```
Hello, Now Start Executing File

Current Directory: /path/to/directory
[✔] Done!
```

### Node.js Script Output
```
Starting Git auto-commit process...
Staged changes.
Committed changes.
Pushed changes to the repository.
All commands executed.
```

## Notes
- Ensure that the Git repository is initialized and set up before running the scripts.
- Modify the file paths and repository configurations as per your environment.

## License
This project is licensed under the MIT License. See `LICENSE` for more details.

