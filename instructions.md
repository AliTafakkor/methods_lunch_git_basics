
# Git and Github Workshop: Session 1

## Project Title: Methods Lunch poster template

**Objective:** By the end of the session, we will have created a poster template for methods lunch page for the next sessions that includes a picture, session details (abstract, time, and location), and styles using CSS. We will learn how Git handles text-based files (HTML/CSS) and binary files (images).

---

## Instructions:

> 🚧 The following instructions assume you have git installed on your device, if not please install git before you start.

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
    This indicated we have a new file (that's untracked) and that the `poster_template.html` has been modified.

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
2. Open `styles.css` in your editor and add the following code to style your webpage:

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

    .info p {
        font-size: 1em;
        color: #FFFFFF;
    }

    .info strong {
        color: #FCF05E; /* Western Gold */
    }

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

This will style the webpage by centering the text, adding background colors, and applying basic formatting.

### Step 6: Stage and Commit the Files
1. Stage the newly added files:
   ```bash
   git add index.html styles.css workshop.jpg
   ```
   
2. Check the status of your repository to see the staged files:
   ```bash
   git status
   ```

3. Commit the changes:
   ```bash
   git commit -m "Add initial HTML, CSS, and image files for the workshop page"
   ```

### Step 7: Set Up a Remote Repository on GitHub
1. Go to [GitHub](https://github.com) and create a new repository named `workshop-ad`.
2. Copy the repository URL (HTTPS or SSH).

### Step 8: Link and Push Your Code to GitHub
1. Add the remote repository:
   ```bash
   git remote add origin <repository-url>
   ```
2. Push your local changes to GitHub:
   ```bash
   git push -u origin main
   ```

### Step 9: Test Your Web Page
1. Open `index.html` in your browser by double-clicking it or running it on a local server.
2. Verify that the page displays the workshop image, the title, and the details.

---

### Recap:
Participants will create:
- **An HTML file (`index.html`)** to advertise the next workshop.
- **A CSS file (`styles.css`)** to style the webpage.
- **An image file (`workshop.jpg`)** to demonstrate that Git can handle binary files like images.

This exercise will showcase how Git works for text and binary files while giving participants hands-on experience with basic Git operations (initializing, staging, committing, pushing).
