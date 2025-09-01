# Template Your Own Clean, Precise Boilerplate Code: No AI, No Wallet Drain.

## Introduction

This is the first part of a two-article series, where we'll explore Microsoft's approach to implementing project templates.

In the second (upcoming) part, we'll cover how to build our own custom template project, including initial files with placeholders for custom names.

### The First Mile of 100

Starting a project from scratch is one of the most thrilling feelings for any developer. It's like standing at the starting line of a 100-mile run, full of energy, confident you'll go the distance. And when you finally reach the finish line, the sense of reward is unmatched. But just like in running, the first stretch feels awkward. Your muscles need time to warm up, and you have to find the right rhythm and pace before things start to flow naturally.

The same happens when you kickstart a project. You don't get into the flow state right off the bat, there are plenty of tasks to handle before that, like creating a clean project, naming it properly, building the project and folder/file structure, installing basic dependencies, setting up references between projects, creating documentation files, and more. And this is just a small portion of the long list you need to complete before you can fully dive into writing code for your application.

This is especially true when you have to build similar applications repeatedly, projects with similar structure, dependencies, and requirements, or when you want to maintain consistent basic standards across all your apps.

### I Know You're Not a Fan of Repetitive Work

Neither am I. We're engineers, for crying out loud, we're designed to automate things for others. So why hold back when it comes to automating something for ourselves? We're even laughed at pretty often when we spend hours or even days automating a task that might take only a few minutes. But what they don't realize is that we're playing the long game. When you automate tasks, you can save days of work over the course of a year, which adds up to a lot.

### So Why Go Manual When AI Can Do the Work?

That's a legitimate question. AI seems to be the answer to literally everything these days, doesn't it? And if you don't use it extensively, you'll be left behind!

Just kidding...

Actually, it's completely up to you. If delegating this task to AI gives you more convenience and saves you a ton of time, more power to you—go for it.

Me? I still like doing it myself, and there are a few reasons why:

#### 1. Precision🎯

I like being a sharpshooter when it comes to coding, especially when automating tasks. Automation usually means you write something once and run it over and over until you need to make a change, which shouldn't happen too often (that's the whole point). With AI, sure, you can get solid results, but how often will it produce the same output every time? It's not precise, and you can't fully rely on it.

#### 2. Cost💰

If you're already using AI agents on a monthly or yearly subscription, this might not matter much. But if you're charged based on the number of prompts you send (cents per 1,000 prompt tokens), doing it yourself could save you a few dollars.

#### 3. Ensuring Quality in Generated Code✅

When you know exactly what your code generator produces, you don't need to spend an extra 30 minutes or so checking everything. That's not the case with AI-generated code—you always have to make sure the basic code matches exactly what you want. Copying and pasting AI-generated code without reviewing it first is a bad idea, no matter how simple or small it seems.

This is especially true for the basic structure, which everything else will be built upon. Changing even a tiny fundamental part later can be nearly impossible, or at least extremely difficult, once other parts of the software are added. So be careful.

If you plan to use AI anyway, I still recommend building the basic structure and setup yourself first, and then leveraging AI to add features on top.

## Enough Talk, Let's Get our Hands Dirty

### How Exactly Does Microsoft Implement Their Default Templates?

As you've probably figured, we'll be looking at examples based on .NET, so if you're a .NET engineer, you're in luck. That said, it doesn't mean you can't apply the same concepts in other languages. The implementation details might differ, but the underlying idea stays the same.

### Let's Recap Some Basics First

Microsoft provides their own built-in templates. When you install the .NET SDK, it includes a set of NuGet packages that contain these templates. This assumes you already have the .NET SDK installed and the dotnet CLI working—something you'll use extensively if you plan to follow the steps in this article.

To check this, simply open your terminal using any CLI tool like PowerShell, Bash, zsh, etc. (I'm currently using PowerShell on Windows 11) and run the following command:

```powershell
dotnet --version
```

![Dotnet version command](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/o5s0t21ynbm69kx75iyk.png)

As you can see, it has outputted the current version of .NET, which in my case is `9.0.102`.

You can also check the installed .NET SDKs by running the following command:

```powershell
dotnet --list-sdks
```

![List of SDKs](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/umhagr11c87jedvv13kl.png)

And runtimes, which can be installed separately but usually ship with the SDK by default, so in most cases, you don't need to install them separately. To check the installed runtimes, run the following command:

```powershell
dotnet --list-runtimes
```

![List of runtimes](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/iofi43kvjberagyyv09x.png)

As you can see, I have a bunch of different runtimes installed on my local machine, which is completely normal. You can have one SDK installed while also having other versions of runtimes on your machine.

As mentioned above, Microsoft provides its own default built-in templates. If you've ever used IDEs like *Visual Studio* or *Rider*, you may have noticed that when creating a new project, the IDE always lets you choose the project type. There are many options, including Console, Web, Testing, Desktop, Class Library, and more. Each type has configurable options when creating the project. In the screenshot below, you can see the supported project types. For example, in a Web project, there are numerous settings you can adjust to your liking, which is both impressive and extremely helpful.

![Rider IDE](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nxkhvvafik4lgz9slaku.png)

What you're seeing in the Rider screenshot is a GUI version of the commands you can run using the CLI. Whenever you use this interface, the dotnet new command runs in the background, creating your project with the initial files.

The highlighted sections show the project types and their respective supported templates. In this example, you can see the templates for Web-type projects.

### Command Line Interface

Speaking of CLI, let's put the GUI tool aside for a moment and take a closer look at the `dotnet new` command. This way, we can understand what's happening behind the scenes.

Let's run the following command to see what options are available with the dotnet new command:

```powershell
dotnet new --help
```

![Dotnet new documentation](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/etm1trwf4zbpe59qeldc.png)

According to the documentation we just retrieved, you can list all the available templates by running the following command:

```powershell
dotnet new list
```

![Dotnet new documentation](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lt3qkf31dxkdx4gyzjjn.png)

We can use this information to generate the project we want. For example, let's create a minimal API called 'BlackBear'.

```powershell
dotnet new webapi -o BlackBear
```

![Newly generated API](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/malw52isthh9a23squaw.png)

And as you can see, it has generated a minimal Web API and used our -o parameter to place it in the specified folder. Our Web API is ready to go, and we can add custom code or modify it however we like.

![Newly generated API](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yc3q7u43h5c7h36mmd4a.png)

## Let's Pop the Hood

Basics and essentials are great, both the editor GUI and the command line interface make our lives easier, which we often take for granted. But why not peek under the hood and see how everything actually works? Better yet, let's pop the hood and disassemble the engine. We want to reverse-engineer this thing so that everything makes more sense.

First things first, let's find out where in the file system these templates are stored. As mentioned earlier, these templates are just NuGet packages that come with the .NET SDK when you install it.

You can locate the template packages using the following paths:

On Windows 11:
`C:/Program Files/dotnet/templates/<version>`

On macOS:
`/usr/local/share/dotnet/templates/<version>`

On Linux Mint:
`/usr/lib/dotnet/templates/<version>`

***⚠️Important: In some cases, these paths might differ, so keep that in mind. These are the paths I've found on my personal computers running Windows 11, macOS, and Linux Mint. Also, `<version>` is just a placeholder, you'll find a folder corresponding to the installed version.***

Let's navigate to this directory and take a look at its contents:

```powershell
ls 'C:\Program Files\dotnet\templates\9.0.1'
```

![NuGet packages](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/612zdwv9cmx5moskx02m.png)

As you can see in the screenshot, there are several different NuGet packages. These packages contain the template implementations. And guess what? You can actually unzip them and explore their contents, that's what I meant when I said we were going to disassemble the engine.

Before we do that, let's quickly go over what each of the NuGet packages does and understand their primary purpose.

### Full Project Templates

####📦 microsoft.dotnet.common.projecttemplates.*.nupkg

These are the core templates used most commonly. They're language-agnostic, the template can be generated in multiple languages: C#, F#, or Visual Basic, while the project type remains the same. Instead of having separate template packs for each language, the common pack bundles all three.

```powershell
dotnet new console -lang C#
dotnet new console -lang F#
dotnet new console -lang VB
```

Supported templates: `console`, `classlib`.

####📦 microsoft.dotnet.web.projecttemplates.*.nupkg

Contains templates for generating web-based applications.

Supported templates: `blazor`, `blazorwasm`, `web`, `grpc`, `razorclasslib`, `razor / webapp`, `mvc`, `webapiaot`, `webapi`, `worker`.

####📦 microsoft.dotnet.test.projecttemplates.*.nupkg

Contains templates for generating unit test projects.

Supported templates: `mstest`, `mstest-class`, `nunit`, `nunit-test`, `mstest-playwright`, `nunit-playwright`, `xunit`.

####📦 microsoft.dotnet.winforms.projecttemplates.*.nupkg

Contains templates for working with WinForms.

Supported templates: `winforms`, `winformscontrollib`, `winformslib`.

####📦 microsoft.dotnet.wpf.projecttemplates.*.nupkg

Contains templates for Windows Presentation Foundation (WPF).

Supported templates: `wpf`, `wpflib`, `wpfcustomcontrollib`, `wpfusercontrollib`.

### Item Templates

####📦 microsoft.dotnet.common.itemtemplates.*.nupkg

Contains smaller items, not whole projects. These items can be added into the an existing project using the same `dotnet new` command.

Supported templates: `buildprops`, `buildtargets`, `class`, `editorconfig / .editorconfig`, `enum`, `gitignore / .gitignore`, and many more...

Examples:
```powershell
dotnet new gitignore
dotnet new globaljson
```

So the next time you'll need a gitignore file, you know how to do it the easiest and the most elegant way.

####📦 microsoft.dotnet.web.itemtemplates.*.nupkg

Contains smaller items, not whole projects, focused on web-related projects.

Supported templates: `apicontroller`, `mvccontroller`, `proto`, `razorcomponent`, `page`, `view`, `viewimports`, `viewstart`.

Examples:

```powershell
dotnet new razorcomponent
dotnet new page
dotnet new viewimports
```

## Breaking Down the Machine to Discover Its Parts

Let's unzip each NuGet package and see what's inside.

The best part? We don't even need to leave the terminal. PowerShell has a handy `Expand-Archive` command that can extract the full contents of a package. Since a .nupkg file is essentially just a .zip file, unpacking it is straightforward.

There’s one small catch: PowerShell expects the file extension to be .zip. That means we'll need to rename the .nupkg file before extracting it. Luckily, this is quick and easy.

⚠️ ***Important: Always copy the package files into a temporary folder before making any changes. You don’t want to risk corrupting the originals inside the dotnet installation directory.***

Here’s the plan:

1. Create a folder named temp (or any name you prefer). Place it somewhere safe, like your desktop, away from system folders.

2. Copy the desired NuGet package into your temp folder.

3. Rename the .nupkg file to .zip.

4. Use `Expand-Archive` to extract the .zip and inspect its contents.

Let's pick one NuGet package and go through the steps one by one.

In my case, I'll use `microsoft.dotnet.web.projecttemplates.9.0.9.0.1.nupkg`

First, we need a new temporary folder. You can create it either through your file explorer or via the command line. I'll stick with PowerShell for consistency.

Start by navigating to the location where you want to create the temp folder:

```powershell
cd '~/Repositories/DevCommunity'
mkdir Temp
```

This will create a new folder where we'll copy our .nupkg file.

Now let's copy the NuGet package into the newly created folder:

```powershell
copy 'C:\Program Files\dotnet\templates\9.0.1\microsoft.dotnet.web.projecttemplates.9.0.9.0.1.nupkg' .\Temp\projecttemplates.nupkg
```

![Files](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0i05ng00apa5ymvr1cro.png)

Now that our NuGet package has been copied, I've given it a shorter name (projecttemplates.nupkg) for convenience.

The next step is to convert it into a .zip file. Since a .nupkg is essentially just a zip archive, all we need to do is rename it from projecttemplates.nupkg to projecttemplates.zip. This can be done easily in PowerShell with a simple rename command.

```powershell
cd .\Temp\
Rename-item projecttemplates.nupkg projecttemplates.zip
```

![Files](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hbxywqsfvqihtp563ls9.png)

Our .zip file is now ready to be extracted. To unpack its contents, run the following command:

```powershell
Expand-Archive -Path "projecttemplates.zip" -DestinationPath "."
```

Now let’s take a look at what’s inside.

![File contents](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/flxbs9r1upa5o3kl33ge.png)

Now, navigate to the content folder and you'll find subfolders for each template under this project type. You can explore any of them. Let's pick the `WebApi-CSharp` folder. You can open it in your favorite code editor. I'll use VS Code.

![VS code](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9s351r4okz6uu0n7zt1g.png)

As you can see, this is the template that gets generated when you create a Web API application. If you're a .NET developer, it'll look very familiar. This is the source of that handy template you use every time.

A few things might seem a little mysterious or unfamiliar. For example, the `.template.config` folder. I bet you haven't seen it in a real project before, right? That's because this folder is specific to template repositories. It's where you configure everything your template should do.

If we open that folder, we'll see several subfolders and three JSON files. The main file is `template.json`, this is where all the configuration for the template is defined.

⚠️Spoiler alert: When you create your own custom template, you should follow a similar structure. In the project root, create a `.template.config` folder, add a `template.json` file, and you'll be ready to start configuring your template, though that topic will be covered in part 2 of this series. So if anything looks unfamiliar here, don’t worry—everything will become clear in part 2 of this series.

![VS code](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ns4ldb1f9pl8isv3tbnb.png)

## What to Expect in the Upcoming Part 2?

This part focused on how Microsoft implements template projects, which are available for us to use. These templates are intentionally general, and for a good reason—they need to be useful for everyone. Every company has its own requirements and standards, and a template shouldn't be too specific or niche. Otherwise, developers would spend hours modifying it, defeating the purpose of using templates in the first place.

In Part 2, we'll create our own customized template and configure it. We'll also explore how to package it as a NuGet package, making it easy and convenient to download and install.