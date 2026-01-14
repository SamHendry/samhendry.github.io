---
created: 2025-08-19
---
Hi friends! I'm Sam, the "Tech Innovation Intern." At Common Sense I investigated two curiosities: can we build interactive content in house, and how does AI enable rapid development and prototyping? To answer these questions, I used AI tooling to built a fully functional web game that teaches kids AI detection skills (yes, there is irony here). I worked with both educators and developers on staff to ensure the quality of the game, code wise and content wise. As Common Sense plays with the idea of creating interactive content, I hope that my work can be a case study of what is possible. This document details what I learned.

The [game](https://commonsense-org.github.io/games-poc) (link subject to change)—adapted from "Two Truths and AI," an idea from *Out of the Box Days* that caught everyone's attention. 

>[!quote] Paraphrased from Lauren
>Parents don't just want to be told what to do, they want to be shown what to do, to see content in front of their kids that they can have a conversation about. They want this teaching moment to be "not stupid."
## The Developer's Shifting Role
For now, AI will not eliminate the developer. There exists a language barrier between designers and the development world that makes it really hard for people without technical knowledge to effectively vibe code. This is best demonstrated by these (increasingly frustrated) prompts from a designer working on the original prototype of *Two Truths and AI*:
%%[link](https://docs.google.com/document/d/1hDy3fRquiR8n0k3KTvPY2y-dRCx0uQXXSfja3Wshy1k/edit?tab=t.0) to the google docs with the chat history %%

- Can you run this game code?
- How do I run it?
- Isn't there a way to run via command prompt?
- I thought there was a way to type "cd" and "npm run" to launch it?
- Is it easy to convert node.js to html?
- Okay, let's keep it simple, could you tell me how to launch it again?

And also (cursor responses paraphrased for your enjoyment):

`User` Can you look through the code and make sure the load times are quick as possible, so all the images load at once and quickly?
`Cursor` I'm gonna prefetch all 30 images at the start of the game! I'll also lie to you about the speed improvements when I actually broke the application.
`User` Hm. Nothing is loading now.
`Cursor` Shoot, you caught me, I'll fix it.
`User` The load times are still weird, is it the file size of the images?
`Cursor` Yes! I can't believe I didn't notice the ridiculously large images you uploaded - 59MB!

%%
Generally embarrassing stuff from the [chat history](https://docs.google.com/document/d/1hDy3fRquiR8n0k3KTvPY2y-dRCx0uQXXSfja3Wshy1k)
- How do I delete files in repo?
- Where is this stuff on my computer, I can't find the original folder?
%%
And a funny case where the designer asked to be able to upload images themself (to be static content), and the bot spit out a version of the application where the *users* were able to upload their own images. The following prompt read: "Remove the upload capability for the user but keep the backend ability to upload." Developers can see the stumbling in language here, but the designers are grasping at straws. When the designer does not know *technically* what they want, the AI will return something working but arbitrary, whereas a developer would return code to company standards. Engineers do things that designers don't even know to ask for!

The designer was able to eventually create a working prototype of the game, but not after around 500 pages of chat history had accumulated. The [prototype](https://erikkhood.github.io/two-truths-and-ai-v.2/) works remarkably well!

That said, AI *will* change the role of the developer, in the event they decide to use it. Vibe coding, in the hands of someone who knows what good code and architecture look like, can be an intriguing tool. Here, **the developer becomes more like a translator**, using the language of engineering and the designer's direction to prompt the AI. Instead of writing all the code from scratch, they spend more time reviewing code. In fact much of the potential speedup that AI can provide you hinges upon if you are faster at reviewing code than writing code. This includes down-the-line cost, as unmaintainable code you generate in two minutes will not save time if you have to maintain it for five years. All in all, the cornerstone is that the developer *articulates* the idea such that it is conducive to good engineering.

With this review-first approach, **AI puts the role of a *senior* developer into the hands of everyone**. Code review in traditionally done from a higher standpoint, by someone with an experienced eye—knowledge of architecture and how all the pieces fit together. This can be a little bit risky for less experienced developers because they have less ability to spot bugs and unmaintainable code in a sea of ostensibly good generated output. Additionally, junior developers are less opinionated on what good code and architecture looks like, simply because they have not seen enough of it yet. In this case, they risk letting AI define what good code is for them, as LLM code becomes their primary teacher. I've always wondered if I'll start to hear more of the speech patterns emblematic of LLMs in real people because generated language is becoming so ubiquitous. The same goes for code.

%%
- [your brain on chatgpt](https://www.media.mit.edu/projects/your-brain-on-chatgpt/overview/?j=9880125&sfmc_sub=318577940&l=5124370_HTML&u=250825141&mid=6409703&jb=0&utm_medium=email&utm_source=Common+Thread+Internal+Email++-+June+-+20250710#faq-is-it-safe-to-say-that-llms-are-in-essence-making-us-dumber)
	- significantly different brain patterns, shifts the cognitive load of your work. Review is traditionally the role of the senior engineer, and now it is the role of the junior.
	- brain engagement scales down with the amount of tooling you use
	- ownership and ability to quote your code fall?

Also Erikk is an exception case of a designer because he thinks very technically and is tech interested
%%
## Generated Code Quality
In the world of AI, understanding architecture becomes really important. I am worried about students who stop after picking up the practicalities of coding, but refrain from learning the whole jigsaw. Those might be the ones that are getting put out by LLMs. For the developers that have a good idea of how all the pieces should fit together, using AI to craft the individual pieces can be helpful.

Unlike when I used AI in previous years, I found that broken code isn't the problem anymore. Models have improved and we have agents now, which iterate upon themself and even check your terminal window to debug. The problem is now extraneous or unmaintainable code. When you prompt a language model, you generally specify the idea but leave out all the engineering done for engineering's sake. This includes, but is by no means limited to: optimization, prefetching, accessibility, styling, typing, state management, rendering strategies, and the UI itself. The more time you spend writing these specs into the prompt, the more time savings you negate from using AI. At a certain point you should just write the function/component yourself.

**Managing this gray area between what you ask for, and what the AI guesses you want, is an exercise in compromise**. Generated code is of *decent* quality, but it's up to you to determine its longevity and efficacy.

When I generated the initial version of the app, it came pre-loaded with a lot of functionality that I ended up removing. It included all the "could be nice" features like user logging with express.js backend I didn't need. It also used an arbitrary architecture that I ended up swapping out with something more conducive to static site generation.

On this front, it is worth the time it takes to **figure out your high-level mainstays—architecture, framework, dependencies, and application requirements—*before* you start generating**. Once you erect the scaffolding, LLMs have the easier job of making specific components and files to fill in. These individual pieces are better defined problems (which LLMs like) because they are downstream from the big-picture architecture you already figured out. You do not want to refactor an entire codebase, it's much easier to review a couple files than it is to change architecture.
## Saving Time
In order for AI to speed up development, you need to use as much unadulterated generated code as possible. The less you need to touch the LLM's output, the faster you can move. This is a simple framework, but I find the exceptions to it to be, well, exceptional. The best approach I've found is to **treat AI like an intern**. To give it a well-defined project within an intentional scope, advise on general plans/architecture, and let it wade through the specific implementation for you to review later. Ironic, because I'm also an intern. When I initially generated the game *without* detailing architecture it took:

- one day to generate the first version and get it running
- another day to read through the codebase and do initial edits
- yet another day to clean up all extraneous functionality
- and even another when I decided to change the framework for hosting reasons

Though I got a working build on the first day, I spent a lot of time navigating the unfamiliar codebase, negotiating with AI's idiosyncrasies, and paying for my previous lack of specificity. However, this pace is still very good. In less than a workweek, I had a prototype I was confident in. 

Another thing to note is that **AI changes the timescale of development**. It decreases up front cost, but increases maintenance cost down the line. Initial generations are speedy, but iterations on top of them fall in effectiveness really fast. LLMs seems to be more concerned with validating you than being correct. If I try, I can usually convince it to give a certain answer, or direct it away from a previous one. It's responses are largely half-truths, things that are technically true, but may have some weird underlying nature. For example, when I prompted to submit a answer immediately upon selection instead of using another button, it just used the two functions (select and submit) right after each other, instead of combining them. Or when I asked it to remove credential handling and it removed the explicit credential code, but missed the adjacent 401 error handling. Here we see, again, that artificial intelligence is no substitute for developer expertise.

Off of a vague prompt, sometimes it can get things right first try, and sometimes it runs in circles for hours (speaking from experience). **By figuring out architecture up front and giving it well-defined problems, AI is less of a wild card**. 
## Suggested Use
I see the two distinct use cases for AI, that in my opinion should be kept separate:
1. Prototyping to communicate an idea (by a designer)
2. Developing to fast-track games to production (by an engineer)

The former's usefulness was demonstrated by the game presentations in [Out of the Box Days](https://commonsense.zoom.us/rec/play/569JtjUhe032K_CZyXghFy64XHy10HpY9dBQRqdQLNdDbYiG_xFxQPBdv6PVtjt4FU8c0g_ASLzRKur2.I5H0Toj17UhDXG1H). The three presented games were vibe coded by designers, and communicated their ideas effectively. Vibe coding provided the designers a language  to explain their idea in a new way, a way more imperative than descriptive.

The latter is what I have detailed, and can be reduced to these guidelines:
- **Define your architecture before using AI**. Specify the stack, dependencies, and high-level functionality you want and use these as context in prompts. You can even write a document spec and attach it as context to every prompt, Replit actually does this automatically.
- **Get a generation right from the first prompt**. LLMs are less useful for revision because they are too preoccupied with validating you, and they tend towards surface-level short term fixes. You want to edit as little generated code as possible to speed up your workflow.

Recommended **Tooling**:
- For Designers, Replit is a useful tool, although it is the most expensive. On the other hand, Two Truths and AI, the game I expanded upon, was first made in Claude, then moved to Cursor for iterations. However, this was an exceptional case because the designer was tech-interested and thought very technically, which is not always the case.
- For Developers, do not use Replit, it is designed to be a walled garden and it is by far the most expensive. The starter plan is 25\$/month and a single agent prompt can cost upwards of a dollar. I had a great experience with GitHub Copilot, which runs at 10\$/month and premium requests are only 5¢. Other than that, use whatever model is the easiest for you and integrates into your workflow, they are all pretty good. 

Lastly, I had a really interesting conversation with Lauren about what kind of interactive content this development strategy would be good for. It seems that it is conducive to module-style games as opposed to immersive-world games. It works better for bite-sized pieces of interactive content, where maintainability is less of a problem as they are not being expanded upon in the future. The workflow that I settled into seems to also benefit this kind of game. I worked closely with Erikk, the brilliant education content manager, for game content and design, and translated his ideas to code on my end. We were able to work really fast and bounce ideas off each other 1:1 to create this game prototype. Since this setup worked so well for us, it is worth thinking about how designers interact directly with engineers.
## Closing Remarks
It was a really rewarding and enjoyable experience building this game. It was so satisfying to see my ideas blossom in real time and I believe in the quality of the content I produced because of the amazing people I worked with.

Lastly, I would like to acknowledge the limits of this exercise. The AI industry is rapidly evolving and a lot could change in the coming years. Models could get better, or they could get more expensive. My personal prediction is the latter will become much more significant. Additionally, there *are* externalities to using these power-hungry LLMs and that should be taken into account. While generating the game data I got a sense of dread thinking about the environmental consequences of such intense AI use. From this worry, I found in some cases using vim macros is just as efficient as using AI. Prompting is not the be-all end-all for development, especially in the face of the resources it takes. And to end it all, I hope AI does not lead to neglecting people. I think a reason that capital is so interested in AI is because its labor is more exploitable than a person's. From a humanitarian standpoint, AI should never be *replacing* people, it should be *assisting* them.
### Next Steps with the Game
If the game continues to be worked on, I imagine the next steps with it will be:
- Data collection and analytics: figure out if the game is actually teaching what it sets out to and balance the difficulty levels with user testing.
- Working on Architecture: I proceeded with a some non-ideal code, especially in the state management department. Some work is needed to make it more maintainable.
## Credits
Thank you to all those that have made this internship experience so rewarding. To Ashwin, Diego, and Lauren for steering the ship and guiding this project. To Erikk for the beautiful game content (as well as his availability through endless iterations). To Ochen who read my code and expanded my development vocabulary. To Nikki and Paloma, who got me into and set up at CSM. And to Andy, who sent me the internship application link at the very beginning.