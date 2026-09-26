<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect a GitHub Repo with AWS

**Project Link:** [View Project](https://nextwork.ai/projects/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_dd9d254e)

## Introducing Today's Project!

In this project, I set up a Git repository for a web app's codebase to learn the fundamentals of Git and GitHub, and how they're used in DevOps workflows.

### Key tools and concepts

Services I used were GitHub, Amazon EC2, keypairs, and VSCode. Key concepts I learnt include setting up a GitHub repository, the difference between Git and GitHub, commands for staging, saving and pushing changes, and setting a a remote origin and branches.

### Project reflection

This project took me approximately 2 hours, including demo and troubleshooting time. The most challenging part was learning the core Git commands init, add, and commit, along with connecting to a remote origin. The most rewarding part was seeing the README tie everything together.

I did this project today to learn more about Git and GitHub  and because it's Day 2 of the 6-Day DevOps Challenge!

This project is part two of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow.

## Git and GitHub

Git is a version control system that tracks changes made in code. It tracks every change you make, which lets you go back to an earlier version of your work if something breaks. I installed Git using the commands  'sudo dnf update -y and sudo dnf install git -y'.

GitHub is a platform that lets us store, share, and collaborate on code. The name comes from combining "Git" (the version control tool it's built on) with "Hub," since it acts as a central hosting place for repositories and collaboration features like pull requests and issue tracking. I'm using GitHub in this project to store the web app's code

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_efaadbf7)

## My local repository

A Git repository is like a folder that tracks every version of your web app's code over time. It's the go-to place for all the code, updates, and changes related to a specific project. GitHub let's you host a copy of it online so others can access or collaborate on it.

Git init is a command that initializes a directory as a local Git repository, setting up the structure Git needs to track changes and manage version control. I ran git init in the web app project folder to set it up for version control, so I could start tracking changes once I added and committed files.

A branch in Git lets you create a separate line of development from your code, so you can make changes safely without affecting the main branch until you're ready to merge them.

After running git init, the terminal confirmed that Git was initialized and that I'm using the default branch, main.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_7bf21bae)

## To push local changes to GitHub, I ran three commands

### git add

The first command I ran was git add ., which stages all changes in the working directory. The staging area in Git holds the changes you've selected to include in your next commit, letting you control exactly what gets committed rather than committing everything automatically.

### git commit

The second command I ran was git commit -m, which saves the staged changes as a permanent snapshot in the repository's history. The -m flag lets me attach a commit message directly, e.g. "made changes to index.jsp

### git push

The third command I ran was git push -u origin master, which pushes the saved code changes to the remote repository (origin). The -u flag sets origin/master as the upstream branch, so future pushes and pulls can simply use git push or git pull without needing to specify the remote and branch each time.

## Authentication

When I push changes to GitHub, Git asks for my credentials because it needs to authenticate me before allowing changes to the repository. This confirms that I have permission to modify the code

### Local Git identity

Git needs my name and email so it can attribute each commit to its author. As a version control system, Git tracks every change made to a project over time, and recording who made each change is essential for collaboration and maintaining a clear version history.

Running git log showed that my commits were attributed to a generic 'EC2 Default User' identity instead of my own name and email.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_9a27ee3b)

## GitHub tokens

GitHub authentication failed when I entered my password because GitHub no longer accepts password authentication over the terminal due to the security risks it poses, they now require more secure methods like personal access tokens or SSH keys.

A GitHub token is like a temporary password that grants access to your GitHub account. I'm using one in this project because it lets me safely authenticate to my GitHub repository while in my EC2 instance.

I could set up a GitHub token by visiting the Developer settings in GitHub, and I set one up that expires in about 30 days, and only allow permissions to repositories.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_fa11169d)

## Making changes again

I wanted to see Git in action, so I made another change to my index.jsp file. At first, the change didn't show up in my GitHub repo because I hadn't added, committed, or pushed it yet.

I finally saw the changes in my GitHub repo after running the same three commands again and refreshing the index.jsp page on GitHub.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_6becb2bc)

## Setting up a READMe file

As a finishing touch to my GitHub repository, I added a README file, which is is a document that introduces and explains your project, like what the project does, how to set it up, and how to use it. I added a README file by running the command touch README.md.

My README is written in Markdown because Markdown is a lightweight markup language that lets you format plain text, which then renders as styled text on a webpage. Special characters help you format that text — for example, # for headers, * for text styling (like italics or bold), and [link text](URL) for links

My README file has 6 sections: Table of Contents, Introduction, Technologies Setup (how the web app was set up), Contact, and Conclusion

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_c94976902)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3)*
