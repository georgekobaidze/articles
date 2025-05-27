# Why I Believe 'dotnet run app.cs' Is a Huge Leap Forward

C# is a beautiful language, rich with so many powerful features and possibilities. Over the years, I've used it to build a wide range of applications, and it's been incredible to watch the language evolve and grow. As a long-time C# developer, I continue to be impressed by its versatility and the innovations that keep it modern and relevant.

I know you're expecting a "but" here. So here it is:

But C# still faces one major challenge compared to languages like Python, Rust, and JavaScript — adoption. Despite its power and elegance, C# tends to lag behind in attracting new developers compared to those languages.

For example, when I need to quickly test something out in Python, I don't have to set up a whole bunch of extra files that have nothing to do with the actual logic itself. I can simply create an **app.py** (or whatever you name it) file, and run it, simple as that.

However, the same can't be done using C#. If you want to run a quick code snippet, you need to create an entirely new project containing boilerplate files and code. Let me show you what I mean:


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rf63y0xf4p26rqfih0ge.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/iazsb2vgqy7kaz9uvzum.png)

It has generated a console app that we can use to test things out. If you're a .NET developer, this feels totally natural for you — I have dozens of console applications for various purposes. 

But if you're new to C# or coming from languages like JavaScript or Python, this setup can feel a bit strange. You'll likely find yourself asking questions like

1. What's the **.csproj** file? Do I even need it?

2. Why is there a **Program.cs** file? Why can't it be named app.cs or something else?

3. What's the purpose of the namespace and the Program class? Why is the Main method static and void, and why is it called **Main** (especially if you're not using the simplified syntax that omits these)?

4. What are those **bin** and **obj** folders, and why are they created?

5. Why can't I just write **Console.WriteLine("Hello World");** in a single file and run it directly?

Well, all of those questions are valid, especially if you're coming from a language that lets you run just a single file. It can feel discouraging to learn C# when something as simple as running “Hello World” seems so complicated. Naturally, you might think, if this is complex, how hard will everything else be? But trust me, that's not the case. .NET excels at simplifying complex tasks, and the platform is continuously evolving to make development easier and more intuitive than ever before.

In the [.NET 10 preview 4](https://dotnet.microsoft.com/en-us/download/dotnet/10.0) you can actually compile and run a single C# file without needing any extra setup. You can even add external NuGet packages directly. And that's not all — you can also create more complex project types, like Web APIs, with ease.

For a hands-on demo by Damian Edwards, watch the video below:

{% embed https://youtu.be/98MizuB7i-w %}

I believe this feature is absolutely critical, I've been waiting for it for a long time. Not that it's inconvenient for me personally to create new projects without it, but this improvement is great for .NET's overall adoption. Some might say that .NET is trying to become Python or imitate other languages, but honestly, every language borrows ideas that work well elsewhere — and that's a good thing. It's how languages evolve and get better.

That said, at some point everyone still needs to get familiar with all the default project files that come with .NET. You can't learn .NET in depth without knowing what the .csproj file, or the bin and debug folders, or many other specific things are. However, enabling new developers to intuitively write simple applications from the start can be a powerful catalyst for sparking interest and growing the community.

One area that still needs improvement is speed. Currently, the performance isn't ideal, but as Damian mentions in the video, this is a brand-new feature, and the team is actively working to optimize it. So, let's just give them some time to cook it up.

.NET 10 is going to be awesome!