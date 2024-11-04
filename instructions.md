### Step 10: View the commit history / log
    ```bash
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
    git push origin main
    ```

    Now, you can see the local and remote repositories are synched, the upstream for main has been set, and you can see all files on the remote repository.
