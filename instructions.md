
# Git and Github Workshop: Session 1

## Project Title: Methods Lunch poster template

**Objective:** By the end of the session, we will have created a poster template for methods lunch page for the next sessions that includes a picture, session details (abstract, time, and location), and styles using CSS. We will learn how Git handles text-based files (HTML/CSS) and binary files (images).

---

## Instructions:

> 🚧 The following instructions assume you have git installed on your device, if not please install and configure git before you start.

### Step 1: Set up the project directory
1. Open your terminal.
2. Create a new folder for the project:
   ```bash
   mkdir git_basics
   cd git_basics
   ```

### Step 2: Initialize a local git repository
1. Initialize the repository:
   ```bash
   git init
   ```
   This will initializes the current folder as a git repository, meaning that you can start tracking the files inside this folder.
2. List the content of the current directory:
   ```bash
   ls -a
   ```
   note that the new directory, `.git` has been created by git. Git uses this directory for its internal jobs, so this folder should not be modified manually (only by git commands).

### Step 3: Git status
1. Get a git status. The `git status` command gives you an overview of the current state of your repository. It shows which changes have been staged, which haven’t, and any files not being tracked by Git.
   ```bash
   git status
   ```
2. You should see the following output:
    ```
    On branch main

    No commits yet

    nothing to commit (create/copy files and use "git add" to track)
    ```
    This indicates there is no files to be tracked and no history to be shown.

### Step 4: Create the HTML file
1. Create a new file named `poster_template.html` in the `git_basics` directory:
   ```bash
   touch poster_template.html
   ```
2. Get another `git status`. You'll see the following output:
    ```
    On branch main

    No commits yet

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        poster_template.html

    nothing added to commit but untracked files present (use "git add" to track)
    ```
    Now, you see the new file you created as untracked 
    
3. Open `poster_template.html` in your code editor (e.g. `pico poster_template.html` or `code poster_template.html`) and write the following code:

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Methods Lunch Poster</title>
    </head>
    <body>
        <div class="poster-container">
            <h1>Methods Lunch</h1>
            <h1>[Session Title]</h1>

            <div class="details">
                <p>[Description of the session goes here. Write about the speaker, the topic, and what will be discussed during the Methods Lunch.]</p>
            </div>
        </div>
    </body>
    </html>
    ```
    This basic HTML structure includes a header, and the workshop details. You can open it in your browser to see how it looks (‍‍‍`open poster_template.html`). From now on, the changes made to this file will be tracked by git.

    ![Alt text](<Screenshot 2024-11-03 at 4.40.23 PM.png>)

### Step 5: Track the HTML file

1. Let's begin tracking the file with git.
    ```bash
    git add poster_template.html
    ```

2. Get another `git status`.
    ```
    On branch main

    No commits yet

    Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
        new file:   poster_template.html
    ```
    There are still no commits to be shown, but the status indicates our file is stashed and ready to be committed.

3. Commit the changes (the newly added `poster_template.html` file).
    ```bash 
    git commit -m 'adding the template html file'
    ```
    *The `-m` option indicates the commit message. As you can find in the git help:*
    ```
    -m <msg>, --message=<msg>
        Use the given <msg> as the commit message. If multiple -m options are given, their values are concatenated as separate paragraphs
    ```
    You'll see the following output when you commit:
    ```
    [main (root-commit) d5a3f69] adding the template html file
    1 file changed, 18 insertions(+)
    create mode 100644 poster_template.html
    ```
    This will make a **snapshot** 📸 of the file, so we can compare changes to this version or go back to this version in the future. 

    > 💡 Writing clear commit messages is crucial, as it helps you understand what changes were made later on. It’s also important to develop the skill of deciding which changes to commit individually and which to bundle together.

4. Get the `git status`, again. It should look like the following:
    ```
    On branch main
    nothing to commit, working tree clean
    ```
    All changes have been committed, and the directory is clean.

### Step 6: Add an image to the template
1. Let's add an image to make the poster eye–catching. Download [this image](https://www.20i.com/blog/wp-content/uploads/2022/08/git-blog-header.png) for the git workshop. And, rename it to `poster_image.png`.
    ```bash
    curl https://www.20i.com/blog/wp-content/uploads/2022/08/git-blog-header.png -o poster_image.png
    ```
2. Get the git status (`git status`). You'll see a new untracked file.
    ```
    On branch main
    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        poster_image.png

    nothing added to commit but untracked files present (use "git add" to track)
    ```
3. Before starting to track this image file, let's edit the template to use the image. Insert the following line at line 12.
    ```html
    <img src="poster_image.png" alt="[Session Specific Image]" class="poster-image">
    ```
    The whole file will look like this:
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Methods Lunch Poster</title>
    </head>
    <body>
        <div class="poster-container">
            <h1>Methods Lunch</h1>
            <h1>[Session Title]</h1>
            <img src="poster_image.png" alt="[Session Specific Image]" class="poster-image">
            <div class="details">
                <p>[Description of the session goes here. Write about the speaker, the topic, and what will be discussed during the Methods Lunch.]</p>
            </div>
        </div>
    </body>
    </html>
    ```
    You can refresh your browser, or reopen the file to see the changes.

    ![Alt text](<Screenshot 2024-11-03 at 4.42.15 PM.png>)

4. Get `git status`. It should return:
    ```
    On branch main
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   poster_template.html

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        poster_image.png

    no changes added to commit (use "git add" and/or "git commit -a")
    ```
    This indicates we have a new file (that's untracked) and that the `poster_template.html` has been modified.

### Step 7: See what's been changed
1. It's often useful to find out what has been changed in a file since the last commit or between any couple of commits. Let's see the first case first. Run the following command:
    ```bash
    git diff poster_template.html
    ```
    ```diff
    diff --git a/poster_template.html b/poster_template.html
    index b88ec55..468a02d 100644
    --- a/poster_template.html
    +++ b/poster_template.html
    @@ -9,7 +9,7 @@
        <div class="poster-container">
            <h1>Methods Lunch</h1>
            <h1>[Session Title]</h1>
    -
    +        <img src="poster_image.png" alt="[Session Specific Image]" class="poster-image">
            <div class="details">
                <p>[Description of the session goes here. Write about the speaker, the topic, and what will be discussed during the Methods Lunch.]</p>
            </div>
    (END)
    ```
    The output will show what's been changed in the `poster_template.html`. If the file name is not specified `git diff` will show you all the changes since the last commit.

2. Stage and commit the new image file and the `poster_template.html`.
    ```bash
    git add *
    ```
    This will add all new or modified file to the stage. Or, you can add them one by one.
    ```bash
    git add poster_image.png poster_template.html
    ```
    Then
    ```bash
    git commit -m 'adding poster image to the template'
    ```
3. Now, the `git diff` will return no changes (we just committed the changes).

### Step 8: Add a CSS file for styling
1. Create a CSS file named `styles.css`:
   ```bash
   touch styles.css
   ```
2. Open `styles.css` in your editor (e.g. `pico poster_template.html` or `code poster_template.html`) and add the following code to style the html page:

    ```css
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        background-color: #201436; /* Dark background */
        color: #FFFFFF;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    .poster-container {
        max-width: 80%;
        max-height: 80%;
        margin: 0 auto;
        background-color: #8F55E0; /* Western Purple */
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
        padding: 20px;
        text-align: center;
        border-radius: 10px;
    }

    h1 {
        color: #FFFFFF;
        margin-bottom: 20px;
    }

    .poster-image {
        aspect-ratio: 1 / 1;
        max-width: 60%;
        max-height: 50%;
        border-radius: 50%; /* Circular Image */
        object-fit: cover;
        margin: 0 auto;
    }

    .details {
        margin-top: 20px;
    }

    .details p {
        font-size: 1.2em;
        color: #FFFFFF;
        margin-bottom: 30px;
    }
    ```

    This will style the poster by centering the text, adding background colors, and applying basic formatting.

3. We also need to link this style file to the `poster_template.html`. To do that, insert the following line at line 7 in the `poster_template.html`. 

    ```html
    <link rel="stylesheet" href="styles.css">
    ```
    Now, the html file should look like this:
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Methods Lunch Poster</title>
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <div class="poster-container">
            <h1>Methods Lunch</h1>
            <h1>[Session Title]</h1>
            <img src="poster_image.png" alt="[Session Specific Image]" class="poster-image">
            <div class="details">
                <p>[Description of the session goes here. Write about the speaker, the topic, and what will be discussed during the Methods Lunch.]</p>
            </div>
        </div>
    </body>
    </html>
    ```

4. Refresh or open the `poster_template.html` (`open poster_template.html`) to view the changes. If you're happy with it stage and commit all changes.
    ```bash
    git add * && git commit -m 'adding style to the temlpate'
    ```

    ![Alt text](<Screenshot 2024-11-04 at 9.11.15 AM.png>)

### Step 9: Add more details
1. Let's add more details to the template. Insert the following to the `poster_template.html` at line 17 (right after the descriptions).

    ```html
    <div class="speakers">
        <p><strong>[First Speaker]</strong> and <strong>[Second Speaker]</strong></p>
    </div>
    <div class="info">
        <p><strong>Date:</strong> [Insert Date]</p>
        <p><strong>Time:</strong> [Insert Time]</p>
        <p><strong>Location:</strong> [Insert Location]</p>
    </div>
    ```
2. Add the corresponding styles to end of your CSS file.
    ```css
    .info p {
        font-size: 1em;
        color: #FFFFFF;
    }

    .info strong {
        color: #FCF05E; /* Western Gold */
    }
    ```

3. Refresh or open the `poster_template.html` (`open poster_template.html`) to view the changes. If you're happy with it stage and commit all changes.
    ```bash
    git add * && git commit -m 'adding details to the temlpate'
    ```

### Step 10: View the commit history / log
1. Use `git log` to see the commit history.
    ```bash
    commit 5c79de77b8dd027f97aab4c30714ecaab2da2263 (HEAD -> main)
    Author: Ali Tafakkor <alitafakkor@gmail.com>
    Date:   Mon Nov 4 09:33:39 2024 -0500

        adding details to the temlpate

    commit 4293da9a0fb8643a244aa1761bef9b2c7ae70951
    Author: Ali Tafakkor <alitafakkor@gmail.com>
    Date:   Mon Nov 4 09:15:02 2024 -0500

        adding style to the template

    commit 1c7d7edaa80dfdbeaa72905e1742337039199f6d
    Author: Ali Tafakkor <alitafakkor@gmail.com>
    Date:   Sun Nov 3 17:21:56 2024 -0500

        adding poster image to the template

    commit d5a3f69564a7a85ae4f61c61551da04b8a126d0e
    Author: Ali Tafakkor <alitafakkor@gmail.com>
    Date:   Sun Nov 3 15:36:33 2024 -0500

        adding the template html file
    (END)
    ```

2. Each commit has a unique identifier or a 'commit hash' like `5c79de77b8dd027f97aab4c30714ecaab2da2263`. These strings are used for referring to the commits. For example if we want to see what has happend between the first and the third commit we can use `git diff` as below:
    ```bash
    git diff d5a3f69564a7a85ae4f61c61551da04b8a126d0e 4293da9a0fb8643a244aa1761bef9b2c7ae70951 >> diff.txt
    ```
    
    Since the differences can be long we use `>> diff.txt` to save the output in a file named `diff.txt`. Here is the file content:

    ```diff
    diff --git a/poster_image.png b/poster_image.png
    new file mode 100644
    index 0000000..8d249c5
    Binary files /dev/null and b/poster_image.png differ
    diff --git a/poster_template.html b/poster_template.html
    index b88ec55..280cec9 100644
    --- a/poster_template.html
    +++ b/poster_template.html
    @@ -4,12 +4,13 @@
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Methods Lunch Poster</title>
    +    <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <div class="poster-container">
            <h1>Methods Lunch</h1>
            <h1>[Session Title]</h1>
    -
    +        <img src="poster_image.png" alt="[Session Specific Image]" class="poster-image">
            <div class="details">
                <p>[Description of the session goes here. Write about the speaker, the topic, and what will be discussed during the Methods Lunch.]</p>
            </div>
    diff --git a/styles.css b/styles.css
    new file mode 100644
    index 0000000..93ea818
    --- /dev/null
    +++ b/styles.css
    @@ -0,0 +1,48 @@
    +body {
    +    font-family: Arial, sans-serif;
    +    margin: 0;
    +    padding: 0;
    +    background-color: #201436; /* Dark background */
    +    color: #FFFFFF;
    +    display: flex;
    +    flex-direction: column;
    +    justify-content: center;
    +    align-items: center;
    +    height: 100vh;
    +}
    +
    +.poster-container {
    +    max-width: 80%;
    +    max-height: 80%;
    +    margin: 0 auto;
    +    background-color: #8F55E0; /* Western Purple */
    +    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    +    padding: 20px;
    +    text-align: center;
    +    border-radius: 10px;
    +}
    +
    +h1 {
    +    color: #FFFFFF;
    +    margin-bottom: 20px;
    +}
    +
    +.poster-image {
    +    aspect-ratio: 1 / 1;
    +    max-width: 60%;
    +    max-height: 50%;
    +    border-radius: 50%; /* Circular Image */
    +    object-fit: cover;
    +    margin: 0 auto;
    +}
    +
    +.details {
    +    margin-top: 20px;
    +}
    +
    +.details p {
    +    font-size: 1.2em;
    +    color: #FFFFFF;
    +    margin-bottom: 30px;
    +}
    +
    ```
    You can see that this reflects adding the image to the template and adding the styles, **consistent with our commit messages**.

### Step 11: Revert changes
1. Imagine you’ve made a change that caused your code to stop working properly, and you need to return to a previous commit where everything was functioning as expected. To go back to a specific commit, you can use the commit hash from git log. For example, to revert to the commit `4293da9a0fb8643a244aa1761bef9b2c7ae70951`, run the following command:

```bash
git checkout 4293da9a0fb8643a244aa1761bef9b2c7ae70951
```

2. You'll get a warning that you have moved to 'detached HEAD' state, meaning you are now viewing the repository as it was at that commit. You can refresh or reopen the `poster_template.html` to verify we have reverted to the old commit. If you intend to make changes from this point, you should create a new branch to save your work. We will leave the branches for next session.

3. You can run `git status` and `git log` to notice how the 'detached HEAD' state is indicated.

4. Run `git checkout main` to go back to the most recent version.

### Step 10: Set Up a remote repository on GitHub
1. So far, all your work has been stored locally on your machine, meaning no one else can view or contribute to your repository unless they have direct access to your computer. To make your repository accessible to others and enable collaboration, let’s set up a remote repository on GitHub.

2. Create a repository on GitHub named `poster_template`.

3. Copy the repository URL (HTTPS or SSH).

    ![Alt text](<Screenshot 2024-11-04 at 12.00.42 PM.png>)

4. Link your local repository to the GitHub repository:
    ```bash
    git remote add origin https://github.com/AliTafakkor/poster_template.git
    ```
    > Use your own username!

5. You'll notice nothing has happened in your remote repository, yet.

6. Try to push your commit history to the remote repository:
    ```bash
    git push -u origin main
    ```
    You'll get the following error message:
    ```bash
    git push -u origin main
    To https://github.com/AliTafakkor/poster_template.git
    ! [rejected]        main -> main (non-fast-forward)
    error: failed to push some refs to 'https://github.com/AliTafakkor/poster_template.git'
    hint: Updates were rejected because the tip of your current branch is behind
    hint: its remote counterpart. Integrate the remote changes (e.g.
    hint: 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.
    ```

7. This issue occurs because the remote repository contains files, such as `LICENSE` and `README.md`, that are not present in your local repository. As a result, Git doesn’t know how to reconcile the differences. To resolve this, you need to pull the commit history from the remote repository and rebase your local commits on top of it. You can do this using the following command:
    ```bash
    git pull --rebase origin main
    ```

8. Look at the commit history with `git log` to see what happend.
    ```bash
    commit 8a5e0786b03e99c30cf5ff09c55b6aaf826edecb (HEAD -> main)
    Author: Ali Tafakkor <alitafakkor@gmail.com>
    Date:   Mon Nov 4 09:33:39 2024 -0500

        adding details to the temlpate

    commit cdc3f1e8a045e31deec0c3944addf4e8eb9f547c
    Author: Ali Tafakkor <alitafakkor@gmail.com>
    Date:   Mon Nov 4 09:15:02 2024 -0500

        adding style to the template

    commit 74622a6afd366a158c83f7ff9879bf2c1b80c20e
    Author: Ali Tafakkor <alitafakkor@gmail.com>
    Date:   Sun Nov 3 17:21:56 2024 -0500

        adding poster image to the template

    commit 575a67de5ae71e574e100ce7527f9672a77e90fa
    Author: Ali Tafakkor <alitafakkor@gmail.com>
    Date:   Sun Nov 3 15:36:33 2024 -0500

        adding the template html file

    commit 7863a6aceb6f7922fb7a7e2c0b9d6993e5fbc0d7 (origin/main)
    Author: Ali Tafakkor <alitafakkor@gmail.com>
    Date:   Mon Nov 4 12:00:11 2024 -0500

        Initial commit
    (END)
    ```
    You see that remote history has been added to your local repository. You now have the files that you had only on the remote repository (check that with `ls`). However, the remote/origin HEAD is still behind the local.

9. Try pushing the local commit history again:
    ```bash
    git push --set-upstream origin main
    ```

    Now, you can see the local and remote repositories are synched (use `git log` to verify), the upstream for main has been set, and you can see all files on the remote repository.

### Step 11: gitignore and the last push
1. Let's add the logo of Center for Brain and Mind in the footer. Insert the following to the `poster_template.html` at line 26 (right before the `</body>`).

    ```html
    <footer>
        <img src="cbm_logo.png" alt="Western Centre for Brain and Mind Logo" class="poster-logo">
    </footer>
    ```

2. Add the corresponding styles to end of your CSS file.
    ```css
    footer {
        max-width: 80%;
        max-height: 10%;
        background-color: #FFFFFF;
        border-radius: 10px;
        margin-top: 20px;
        text-align: center;
    }

    .poster-logo {
        max-width: 95%;
        height: auto;
        margin: 20px auto;
    }
    ```

3. Download [this logo](https://www.uwo.ca/bmi/img/homepage/Western-Logos-Centre-for-Brain-and-Mind-Detailed-Horizontal-Positive-RGB.png) for Center for Brain and Mind. And, rename it to `cbm_logo.png`.
    ```bash
    curl https://www.uwo.ca/bmi/img/homepage/Western-Logos-Centre-for-Brain-and-Mind-Detailed-Horizontal-Positive-RGB.png -o cbm_logo.png
    ```

4. Run `git status`, and you’ll notice an untracked file named `diff.txt`, along with other files that we care about tracking. In many projects, there are files we don’t want to track or be notified about when they change, such as temporary files, build artifacts, or sensitive information. This is where `.gitignore` becomes useful.

5. Create a `.gitignore` file in your repository (if you don’t have one already):
    ```bash
    touch .gitignore
    ```
    This will keep a list of files or filename patterns to ignore.

6. Open the `.gitignore` file and add the names or patterns of files you want to ignore. For example, to ignore `diff.txt`, do:
    ```bash
    echo 'diff.txt' >> .gitignore
    ```
7. Run `git status`, again. Now, `diff.txt` should no longer appear as an untracked file. 

8. Refresh or open the `poster_template.html` (`open poster_template.html`) to view the changes. If you're happy with it stage and commit all changes.
    ```bash
    git add * && git commit -m 'adding CBM logo in the footer'
    ```

    ![Alt text](<Screenshot 2024-11-04 at 9.41.49 AM.png>)

   > You may have noticed that it’s helpful to bundle related changes into a single commit. For example, when adding a footer, you should group the updates in both the HTML and CSS files together. This approach makes it clearer and more meaningful if you need to reverse those changes later. While it’s <u>not</u> mandatory, it’s a great practice that helps keep your work organized and your thought process structured. 

9. Finally, push everything to the remote repository.
    ```bash
    git push
    ```

    > It’s a good habit to always pull before pushing, unless you’re absolutely certain that no one else has made changes to the remote repository. This practice ensures your local branch is up to date and helps prevent potential merge conflicts.
    >```bash
    >git pull && git push
    >```

10. Now, if you try `git pull` or `git push`, Git will inform you that everything (all commits) is up to date.

---
Congratulations! **You’ve learned Git!** 🎉 In the next session, we’ll discuss branching, where you’ll discover how to manage and organize your work on different features or fixes without impacting the main project timeline. Keep practicing, and you’ll soon master version control!