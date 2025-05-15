# Kickstarting a .NET Solution from Scratch with the CLI

## Introduction

You can use this article as a cheat sheet or a starting point to mastering the **CLI**.

The CLI is one of the most essential tools in a software engineer's toolbox. As useful as it is, it can feel a little intimidating for many developers (especially on the very first encounter). Others get excited. I remember seeing the terminal for the first time and thinking, "whoa, that looks super cool, I want to master it. NOW!"

But the CLI wasn't built to impress or scare anyone (especially not scare). It was designed to make our lives easier by providing the simplest form of interface possible. As developers, we should always strive for simplicity—our job is already hard enough without adding layers of unnecessary complexity.

The CLI isn't only about simplicity—it's the universal tool. You learn the ropes once, and you can use that knowledge for the rest of your career. Of course, like everything in programming, there's always more to learn, but it's the first steps that are the hardest. Once you get past that, you'll find yourself cruising along, steadily building on what you already know. 

It's a lot like using **chopsticks**: awkward at first, but once you figure it out, you can eat sushi in public without looking like you're trying to solve a Rubik's Cube with your elbows. And just like chopsticks, the CLI isn't just functional — it's cultural. Yes, developers have our own culture, and using the CLI is one of them.

Now let's get back on track. This article isn't about all the benefits of using CLI — that could easily turn into a good 30-minute read. Instead, we're focusing on how to use the CLI to kickstart our .NET project. 

**Spoiler alert:** This is so easy, if it were a boss fight, it'd be the kind with god mode enabled and a neon green 'PRESS ANYTHING TO WIN' button — unless you press the power button, in which case... **GG!** and **git gud** (and for those wondering, "git gud" is definitely not a Git command).

## Why Use the CLI When You've Got All These Awesome Editors?

That's a great question! Those editors are indeed awesome and often come with built-in templates to help you create a complete initial project effortlessly. However, each editor is different and sometimes they're made by completely different companies. For example, [Visual Studio](https://visualstudio.microsoft.com/) is developed by **Microsoft**, while [Rider](https://www.jetbrains.com/rider/) comes from **JetBrains**. These two editors offer very different experiences. When I switched from Visual Studio to Rider, it felt like learning a whole new world, complete with its own learning curve. Even something as simple as creating a new project varies from one editor to another. 

Alright, **ThePrimeagen**, if you're reading this for some reason, I know I should switch to **Vim** and make my life exponentially better. I'm working on it, okay? Let the man cook. 🔥

Additionally, their templates are quite generic. So after generating a new project, you often have to tweak a lot of things to customize it the way you want, which can be a bit inconvenient.

The CLI solves both of those problems.

## Let's Create a New Solution Using Only the CLI and See If It Lives Up to the Hype

The structure I'm going to create is based on the one shown in one of my articles: [Foundational Project Structure for .NET Projects].(https://dev.to/georgekobaidze/foundational-project-structure-for-net-projects-3dn3), Keep in mind, the example here is a simplified version to avoid making this article unnecessarily long.

You don't really need any specific prerequisites, just make sure you have installed the [.NET CLI](https://learn.microsoft.com/en-us/dotnet/core/tools/). If you have the [.NET SDK](https://learn.microsoft.com/en-us/dotnet/core/sdk) installed on your local machine, you're good to go—the .NET CLI comes bundled with the SDK.

1. Alright, first things first: let's create a new folder for the entire solution:

    ```bash
    mkdir DarkMatterApp
    ```

2. Next, navigate into the newly created folder:

    ```bash
    cd DarkMatterApp
    ```

3. Now, let's create our solution file:

    ```bash
    dotnet new sln
    ```

    After this, a new solution file named DarkMatterApp.sln will be created. You can verify it by running the **ls** command.
    
4. Now that the solution file is created, let's create a folder for our source code called **src**:

    ```bash
     mkdir src
    ```

5. And inside this folder, let's initialize a new project. You can create any type of project—console app, web app, Blazor, MVC—you name it. For this example, we'll create a new Web API application using the **dotnet new** command, which accepts various parameters, including the project type. To see all the available project templates, you can run this command:

    ```bash
    dotnet new list
    ```
    
6. After running this command, you'll see a list of available application types. Since we want to create a Web API application, simply run the following:

    ```bash
    dotnet new webapi -o src/DarkMatterApp.API
    ```

    Note that we use the **-o** option to specify the output folder.

7. Now that our application has been created, we need to add its .csproj file to the solution (.sln) file. To explain it simply, a solution file is a kind of container for one or more projects—it defines which projects belong to the same solution. Let's run the following command:

    ```bash
    dotnet sln add src/DarkMatterApp.API/DarkMatterApp.API.csproj
    ```


### Now let's do the same for the tests:

```bash
mkdir tests

dotnet new xunit -o tests/DarkMatterApp.API.Tests

dotnet sln add tests/DarkMatterApp.API.Tests/DarkMatterApp.API.Tests.csproj
```


### Never forget a README file. To create one, write the following command:

```bash
echo "# Dark Matter App" > README.md
```

This command will generate a Markdown file with the main title “Dark Matter App.”

### It's time to configure our local Git repository:

I'm going to assume that at some point you'll want to upload this repository to GitHub, so why not take care of that now? Before initializing your local Git repository, make sure you've downloaded and installed the [Git CLI](https://git-scm.com/downloads). Also, to avoid cluttering your remote repository with unnecessary files, let's add a **.gitignore** file first. It's super easy with the .NET CLI—just run the following:

```bash
dotnet new gitignore
```

And a .gitignore file will be created in your root folder with base content. You can later add any files of your choice that you want to ignore further.



Now initialize the local Git repository:

```bash
git init
```

This command will create a **.git** folder in your root directory, which stores all the information about your repository. From here, you can start committing your code and take advantage of all the powerful features Git has to offer.


To push your solution to a remote repository, you'll need to create one on your GitHub account—duh. Once that's done, run the following commands:

```bash
git add .

git commit -m "Initial commit"

git branch -M main

git remote add origin https://github.com/[your-account-name]/[your-remote-repository-name].git
```

Now you're all set!



## Let's wrap things up with a separate code snippet containing all the commands used in this example, so you can easily reference it later as a handy note:

```bash
mkdir DarkMatterApp

cd DarkMatterApp

dotnet new sln

mkdir src

dotnet new list # (OPTIONAL, to see what project types are available to create)

dotnet new webapi -o src/DarkMatterApp.API

dotnet sln add src/DarkMatterApp.API/DarkMatterApp.API.csproj

mkdir tests

dotnet new xunit -o tests/DarkMatterApp.API.Tests

dotnet sln add tests/DarkMatterApp.API.Tests/DarkMatterApp.API.Tests.csproj

echo "# Dark Matter App" > README.md

dotnet new gitignore

git init

git add .

git commit -m "Initial commit"

git branch -M main

git remote add origin https://github.com/[your-account-name]/[your-remote-repository-name].git # Don't forget to replace placeholders with actual values

git push -u origin main
```

And there you have it—a fully structured .NET solution built from scratch using only the CLI. Simple, clean, and surprisingly powerful. Happy coding and git gud! 🚀