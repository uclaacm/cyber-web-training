# ACM Cyber Web Training
A short training to writing web challenges for ACM Cyber interns & officers! The goal of this training is to provide an overview not only for how ACM Cyber runs and deploys challenges but also to familiarize yourself with common tools used in development for web challenges. The end product of this is that not only will you have written a couple of challenges but also been exposed to Git, GitHub, Docker, Express.js, HTML/CSS, JavaScript and much more.

## 1. Getting Started
To get started with this project, perform the following steps. For this phase, you will need to have Git installed on your computer and a GitHub account created. Visit [https://git-scm.com/](https://git-scm.com/) to download Git and visit [https://github.com/](https://github.com/) to set up an account on GitHub. GitHub Desktop is also recommended if you prefer a GUI. Visit [https://desktop.github.com/](https://desktop.github.com/) to install.

1. Make your own repository on GitHub. Click on "Use this template" and then "Create new repository" on your personal GitHub.
2. Clone your repository. In your terminal run the following command.
```
git clone https://github.com/[YOUR_USERNAME]/cyber-web-training.git
```
3. Move yourself into the directory on your local system.
```
cd cyber-web-training/
```
4. Try making a commit! Below is a common workflow for using Git. First edit one of the files in your repository and run the following workflow.

```
git pull # pull updated changes from the remote repository
git add -A # stage all of your local changes
git status # check your staged changes
git commit -m "your message here" # create a commit and add a message to your commit
git push # update the remote repository with your changes
```

## 2. Writing & Submitting Your Challenge
Inside this repository, you will see `example-challenge/`. This is an example of what a challenge file typically looks like to deploy on the Cyber platform. The required file in each challenge folder is `challenge.toml`, an annotated copy of one of these files is shown below.

```toml
# This is a short abbreviation of your challenge name used to help create the URL for your challenge on acmcyber.com.
slug = "example-challenge"

# This is what your challenge is called.
title = "Example Challenge" 

# This is you! Put your name here! :)
author = "Jerry"

# How difficult your challenge is. Challenge points range from 0-100. 
value = 10

# Your challenge description supporting markdown.
description = """What is the name of the president of ACM Cyber from 2019-2020? Example of challenge [file](file.txt). Example of [link](https://acmcyber.com)."""

# Short abbreviation to descrbe what category your challenge is in. NOTE: You can only put ONE in the list.
tags = ["intro"]

# Any files that you reference in your challenge description. Leave an empty array [] if you have none.
files = ["file.txt"]

# Your prized solution!
flag = "flag{sanjana_aka_death}"

# Whether your workshop is this week or not.
enabled = true
```

**Prompt:** Write a challenge where the flag is a fun fact about yourself! Label it as an "intro" challenge.

1. Clone the challenge repository (ask for the URL).
2. Create a branch for you to work on your own challenge.
```
git checkout -b YOUR-BRANCH-NAME
```
3. Make a copy of this challenge template using the following command. Make sure to move your challenge into the `challenges/` directory later on.
```
cp -r example-challenge/ YOUR-CHALLENGE-NAME/
```
3. Edit the `challenge.toml` file and other relevant files to contain your challenge information.
4. Commit your changes and push your branch to the remote repository.
```
git push --set-upstream origin YOUR-BRANCH-NAME
```
5. Create a pull request. Visit the challenge repository URL and click on the tab that says "Pull Request". Alternatively, there should be a message indicating that you can create a pull request from changes on a recently updated branches.
6. Assign an officer to review your pull request and watch your challenge get merged.

## 3. Developing Your Web Challenge
Inside this repository, there is a sample web application in `app/`. This contains an example Express.js application that is containerized using Docker. For this phase, you need to install Node.js, npm, and Docker Desktop. To install Node.js and npm, visit [https://nodejs.org/en/download/](https://nodejs.org/en/download/). To install Docker and Docker Desktop, visit [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/).

First, try to run the application locally.
1. `cd app/`
2. Install the dependencies. JavaScript applications have dependencies called `node_modules`. These can be added to the `package.json` and `package-lock.json` using a package manager for JavaScript called `npm`. In this case, the dependencies are already added to those files so you just need to run the following.
```
npm install
```
3. Run the Express.js application. Use the following command to run the application. You should be able to visit [http://localhost:3000](http://localhost:3000) to see the application working.
```
node app.js
```

Next, run the application using Docker.
1. Ensure that Docker Desktop is running and open so that the Docker daemon is active.
2. Build the application image. Run the following command.
```
docker build . -t YOUR_IMAGE_NAME
```
3. Run the built image using the following command. Visit [http://localhost:3000](http://localhost:3000) to confirm that the app is deployed.
```
docker run -p 3000:3000 -d YOUR_IMAGE_NAME
```
4. CTRL-C to kill the application.
5. Run the application using docker-compose. The settings for this are in `docker-compose.yml`. Run the following command and visit [http://localhost:3000](http://localhost:3000) to confirm that the app is deployed.
```
docker-compose up
```

**Prompt:** Edit the Express.js application in `app/` to add a few new features to your challenge. Below are some guided changes. Feel free to customize it however you want. Be sure to add this as part of a challenge folder and create a pull request with the challenge.

1. Add an image to the webpage. Copy the following into `public/index.html`. Feel free to add your own image URL (Google Images helps).
```html
<img src='IMG_URL' alt='Here is my image' width='30px' height='20px'>
```
2. Add a pagraph with a CSS selector and stylize it.
```html
<p class='paragraph-text'>Some fancy text</p>
```
```css
<style>
    ...
    .paragraph-text {
        color: red;
    }
</style>
```
3. Add a new endpoint to the Express.js application in `app.js`. Create the `/flag` endpoint to send the flag.
```javascript
// define /flag route
app.get("/flag", (req, res) => {
  res.send("Here is the flag!");
});
```
4. Add your own spin to the challenge!

*Additional Resources*:
- *Express.js Documentation*: [https://expressjs.com/en/4x/api.html](https://expressjs.com/en/4x/api.html)
- *Docker documentation*: [https://docs.docker.com/](https://docs.docker.com/)
- *W3 Schools (HTML/CSS/jS)*: [https://www.w3schools.com/](https://www.w3schools.com/)
- *GitHub Pages (if you just want to deploy HTML/CSS/JS frontend)*: [https://pages.github.com/](https://pages.github.com/).

## 4. Deploying Your Challenge
The last stage of the challenge writing process is deploying it to [https://acmcyber.com](https://acmcyber.com)! This part will only be demonstrated. Reference the documentation to see how to deploy your own challenge!

## Acknowledgements
Thanks to Benson Liu, Stephen Kelman, and Jerry Xu for putting this training together.