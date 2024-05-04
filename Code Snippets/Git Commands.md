### 1. How to copy all file relative paths in a git commit

To copy all file relative paths that were changed in a specific Git commit, you can use the `git show` or `git diff-tree` command. These commands allow you to list the files that were changed in a commit, including paths relative to the repository root. You can then copy these paths as needed.

Here's a step-by-step process to achieve this:

**1. Open your terminal or command prompt:**
First, navigate to your Git repository directory using the `cd` command.

**2. Find the commit hash:**
If you already know the commit hash you're interested in, you can skip this step. Otherwise, you can use the `git log` command to find the commit hash. This command will show a list of recent commits, including their hashes.

**3. Use the `git show` or `git diff-tree` command:**

- **Using `git show`:**
  ```
  git show --pretty="" --name-only <commit-hash>
  ```
  Replace `<commit-hash>` with the actual hash of the commit you're interested in. This command will list the file paths that were changed in that commit, relative to the repository root.

- **Using `git diff-tree`:**
  ```
  git diff-tree --no-commit-id --name-only -r <commit-hash>
  ```
  Similar to the `git show` command, replace `<commit-hash>` with your specific commit hash. This will also list the changed file paths in the specified commit.

**4. Copy the file paths:**
The output of the above command will be the list of file paths that were changed in the specified commit. You can manually copy these paths from your terminal. However, if you prefer to automatically copy them to your clipboard, you can use the following methods depending on your operating system:

- **On Linux/Unix/macOS:**
  Append `| pbcopy` (macOS) or `| xclip -selection clipboard` (Linux, if you have `xclip` installed) to the command. For example:
  ```
  git show --pretty="" --name-only <commit-hash> | pbcopy
  ```

- **On Windows:**
  PowerShell has a built-in cmdlet `Set-Clipboard` that can be used:
  ```
  git show --pretty="" --name-only <commit-hash> | Set-Clipboard
  ```
  Or, if using the Command Prompt, you can use `clip`:
  ```
  git show --pretty="" --name-only <commit-hash> | clip
  ```

Note that automatic copying to the clipboard relies on external tools (`pbcopy`, `xclip`, `Set-Clipboard`, or `clip`) which need to be present and properly configured in your system.