
# Git and Github Workshop: Session 1

## Project Title: Methods Lunch poster template

**Objective:** By the end of the session, we will have created a poster template for methods lunch page for the next sessions that includes a picture, session details (abstract, time, and location), and styles using CSS. We will learn how Git handles text-based files (HTML/CSS) and binary files (images).

---

## Instructions:

> The following instructions assume you have git installed on your device, if not please install git before you start.

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
1. Get a git status:
   ```bash
   git status
   ```
2. 

### Step 4: Create the HTML File
1. Create a new file named `poster_template.html` in the `git_basics` directory:
   ```bash
   touch poster_template.html
   ```
2. Open `index.html` in your code editor and write the following code:

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
            <p>[Description of the session goes here. You can talk about the speaker, the topic, and what will be discussed during the Methods Lunch.]</p>
        </div>
        <div class="speakers">
            <p><strong>[First Speaker]</strong> and <strong>[Second Speaker]</strong></p>
        </div>
        <div class="info">
            <p><strong>Date:</strong> [Insert Date]</p>
            <p><strong>Time:</strong> [Insert Time]</p>
            <p><strong>Location:</strong> [Insert Location]</p>
        </div>
    </div>

    <footer>
        <img src="cbm_logo.png" alt="Western Centre for Brain and Mind Logo" class="poster-logo">
    </footer>
</body>
</html>
```

This basic HTML structure includes a header, an image, and the workshop details.

### Step 4: Add a CSS File for Styling
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

### Step 5: Add the Image Files
1. Download the following image files and save them in your `workshop-ad` folder:

   - **Image 1:** `workshop.jpg` (This can be a placeholder image for the workshop)
     - ![Placeholder Image 1](https://via.placeholder.com/600x400?text=Workshop)
     - Right-click and save this image to your folder.

2. Make sure the images are saved as `workshop.jpg` in your project directory.

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
