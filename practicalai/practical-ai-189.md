**Daniel Whitenack:** Welcome to another Fully Connected episode of practical AI. This is where Chris and I keep you fully connected with everything that's happening in the AI community. We'll discuss a few things that are in the AI news and dig into some learning resources to help you level up your machine learning game. I'm Daniel Whitenack, I'm a data scientist with SIL International, and I'm joined as always by my co-host, Chris Benson, who is a tech strategist at Lockheed Martin. How're you doing, Chris?

**Chris Benson:** Doing great, Daniel. How are you today?

**Daniel Whitenack:** I am doing great. I don't know if our listeners listened to a couple episodes ago, we had a bird family setting up camp on our deck at our apartment, and having two eggs... So one of those eggs unfortunately didn't make it, but one turned into a bird, and that bird flew the coop, and now they have decided to start another family on our porch, because apparently it's a great place to start a family of doves, I guess.

**Chris Benson:** It's the coop. The great hatchery.

**Daniel Whitenack:** Yeah. So I have another chance -- I never got to get out my computer vision kit and cameras and monitoring last time around, so maybe I'll have another chance here... Because I suspect that the same pattern is repeating.

**Chris Benson:** Gotcha. Looking forward to that. You need to post pictures of it, or some video, or something.

**Daniel Whitenack:** Yeah. If anybody has any suggestions out there for alerting or monitoring based on activities of doves in a nest, let me know, and I can set up the Raspberry Pi and all that stuff on my deck.

**Chris Benson:** Excellent.

**Daniel Whitenack:** Chris, every once in a while we get to do one of these shows where we bring out an assortment of topics that have caught our attention over the past couple of weeks, and I think it's a good time to do that, because there continues to be a lot coming out related to infrastructure, and new models, and new products, and all sorts of things... So yeah, good time to do that.

One of the first things I wanted to highlight, which came out from actually a company that was a guest on the podcast a while back, Baseten, released a new open source project called Truss. So if you go to GitHub under basetenlabs, and then truss, you'll find this project, which they kind of market as "A seamless bridge from model development to model delivery, and an open source standard for packaging models built in any framework for sharing and deployment in any environment, local or production." So what are your thoughts when you see this, Chris? What comes to mind?

**Chris Benson:** \[00:04:30.10\] I love it, I think it's very much needed. I've been putting a lot of thought lately into the need to make all of this stuff that we talked about much easier for people to get into... And so I think Truss is a fantastic way of kind of getting that going, moving from environments they're already in, like Jupyter Notebooks, out in production without having to go back to a web framework and do all that work. So it's good stuff.

**Daniel Whitenack:** Yeah. And they include emojis on their readme, so you know it's friendly and accessible.

**Chris Benson:** How can it go wrong...? Exactly.

**Daniel Whitenack:** \[laughs\] Yeah, I've actually -- since we talked with Baseten, I've used their product a little bit... And I know that -- just from looking at this, I'm assuming that they're sort of eating their own dog food, because some of the convenience that's built in their product is - not all of it, but some of it is released in this package, which is pretty cool, and it kind of allows... So there's certainly a lot of frameworks out there to do model serving, or deployment, or like model registry sort of things... Some of them kind of assume that you have a bit of infrastructure chops, I think, to start with... Like maybe figuring out how to run something on Kubernetes, or something like that... And that's a big step for a lot of people. So I think this, that it's really targeting - hey, you're running maybe something in a Jupyter Notebook. How do I export this model and deliver it?

I also think that some of these things around model deployment miss some key aspects. Truss talks about bundling secret management and API keys into their deployments, which I think is really, really important. So it's not that difficult for people to figure out how to build like a Flask app with their model, but then figuring out testing, and deployment, and API keys, and securely managing the API - that's a whole other ballgame. Yeah, I'm really impressed that they've kind of built a lot of this in.

**Chris Benson:** They've put a fantastic capability out in Truss, in terms of being able to address that. It's something I've been thinking about. Right now, as a slight sideline on this, that is relevant, I think - I'm learning something new through beginner's eyes, because both you and I program in several languages, and we came together originally in the Go programming community, which is how we got to know each other... And right now for a different thing I'm learning Rust, and so I've been diving into Rust... But it's forced me back into that beginner mindset, and I've brought that back into these other things that we talked about a lot lately, and I've been looking at a lot of AI and deep learning through that beginner's mindset... And there's such a need; we're still leaving out a lot of people on these capabilities, and things like Truss are amazing solutions. I think we need others as well, just so that people with different levels of skill, different skill levels, and such can find it accessible. So Truss is one part of that solution, it looks like.

**Daniel Whitenack:** \[00:07:55.28\] Yeah. And just to give people a -- since you're listening, a sort of visual picture of what this might look like... If you're in Python, and you create a model, you can import the Truss package, and then sort of use this make truss command or method point to the directory where your model or where your code is, and then that will sort of serialize and package the model and freeze dependencies within a Docker image and all of that, which can be complicated in and of itself. And then you can call that and/or deploy it via a variety of ways. I mean, in clouds, and like really simple ways to run things, like ECS, or GCP Cloud Run. Of course, you could run it in Baseten as well, in their own infrastructure... But it has that -- because it's sort of freezing all of these dependencies and your model package in a Docker image, then you have the ability to run this all sorts of places, whether that's local, or in these cloud solutions, or in Baseten, or wherever.

So yeah, it's I think it's pretty cool, and it's an approachable way to get into this model delivery stuff for those that maybe are hitting that pain of "Hey, I've got my model in a Jupyter Notebook, but I don't know what to do next" sort of situation.

**Chris Benson:** So I have a random question for you...

**Daniel Whitenack:** Sure.

**Chris Benson:** As we're looking at things like Truss and recognizing that most of our community here is mainly Python-oriented for the development stuff, do you think that anytime soon we will start expanding some of the development and then deployment and packaging tools into other languages? Do you think that's likely? Or do you think we have a way to go before we get to something where we're starting to look at kind of a multi-language community, rather than the Jupyter focus we've had for so many years?

**Daniel Whitenack:** Yeah, it's an interesting question... I think there's certain sets of tooling... I know that there's tooling now in Go where you can import like Hugging Face transformers models and such... And so there's more interoperability. There's certainly a lot of ways to run models in various other systems, or languages, like JavaScript, or Go, or Rust, or other things... But that kind of like \[unintelligible 00:10:26.06\] workflow...

**Chris Benson:** I think so.

**Daniel Whitenack:** ...in my mind still seems very much Python-focused. I don't see a lot of motion away from that. I do see certain trends happening... Language things seem to be more focused on Python now, in terms of the model development side, and maybe like interoperability on the inference side. Are you seeing similar things?

**Chris Benson:** Yeah, that seems accurate to me as well. Yeah, I am. It's just -- going back to my Rust learning experience, as I'm having to delve out of something I know well, and into something that puts me back into first grade, so to speak, I've been thinking about the fact that we're still leaving behind communities of people... And I'm really curious to see what other options some different organizations or companies, or just inventive individuals come up with, to let us be more inclusive with people that maybe don't traditionally have this space accessible to.

**Daniel Whitenack:** Yeah. Just out of curiosity, Chris, what has your experience been like with Rust?

**Chris Benson:** \[00:11:42.06\] Well, without taking us too far off the main line of our topic area, just as a new thing, they take a different approach. It's one of those languages that always wins the most loved when people are rating their languages and stuff, and I can see why... But it is a substantial learning curve, and it has made me very empathetic to people who are having to deal with other learning curves, such as this one, that we're talking about in general... Because unlike Go, which tends to be fairly small by design, and kind of have one way of doing everything, and does some stuff for you that's pretty nice, Rust kind of takes the opposite approach and gives you every possible option out there to optimize what you're doing... Which is important for certain use cases, including one that I'm working on. And so it's been interesting, it's put me back in the "I'm going to take a big thing and learn it new", and it made me think about if you're not a Pythonista and super-savvy in the juxtaposition of where Python intersects with the deep learning world in general... We're still in a moment where this really huge, important field that's revolutionizing technology is still quite inaccessible to a lot of people, I think. And so it's just a reminder; that's why it's on the top of my mind today.

**Break:** \[00:13:03.27\]

**Daniel Whitenack:** Well, thinking about this model delivery side of things, it gets me thinking also about how -- you know, we've seen an increasing number of things in the news, and in conversations about ML Ops, and GitOps, and CI/CD impacting kind of AI and the ML world, and people thinking more about this operations side of things... I wonder -- you know, I still encounter a lot of AI practitioners or data scientists who are really kind of trying to get a grip on what is CI/CD, and how does that side of automation -- or how should it or could impact their development workflows... It might be worth talking for a second about CI/CD, and what that exactly means, and how it might impact practitioners' workflows. What do you think?

**Chris Benson:** I totally agree with you. And we've actually talked a little bit about this on previous episodes, about the general feel that there has to be a convergence between CI/CD and ML Ops, instead of them being kind of thought of as separate subfields, if you will... Because we're going into a future where they're not two totally separate things that are always on their own tracks, and on their own infrastructures. Models are going to be in everything we do going forward, so the idea of software and models being completely separate with their own infrastructures is a little bit -- I don't know, it seems antiquated to me.

I think there's a movement that we're seeing right now, where ML Ops and CI/CD in general are starting to come together, as people realize that, "Yes, I'm going to be deploying software, and yes, I'm going to be deploying models, most often, and they will be happening together and at the same time, and so therefore, I must have something that works for all of the above." I think that that's a bit of a challenge... If for no other reason, there's some cultural differences in how we approach and what the priorities are, and stuff... And so there's kind of two worlds smashing together, trying to find something that works for all.

**Daniel Whitenack:** So Chris, I want to maybe describe some of what I've been doing recently with this intersection of automation in CI/CD and machine learning or AI models, and I'd love to get your critique of that, and help me know how I can do better, or maybe just initial thoughts...

\[00:16:01.03\] So a lot of what we've been doing recently - and we're always kind of tweaking this workflow - is we have an ML Ops solution, and we're really thinking of that ML Ops solution as our experimentation and model training platform. So this is where a lot of jobs will necessarily fail, because we're trying weird and crazy things, and we have queues of GPUs where we can queue up experiments and train new models, or do pre-processing of new datasets... Eventually, we get to a state where we sort of figure out what we're doing, and we know there's a certain type of model that we are training successfully, and would like to integrate into some system or service that we support. And so our ML Ops solution kind of provides as output of these training jobs a hash of a bundle, that is like the model bundle output that we have trained. So by hash, I just mean like a series of numbers, letters that points to a unique bundle that we've trained. And so we can look up in our ML Ops system, this model bundle, whatever the hash is, was trained on this date, with this model, and this is how the task went, and all that. And it connects also back to our Git repo, where we have the training code with the exact commit ID that trained that model. So we've got like the code that trained it, the output of the model and the hash of that model...

But then that's -- the Truss project I was just talking about, that's not like model delivery, right? So in terms of connecting more to the CI/CD things, at that point our model is really just like an artifact is used in software, in various software functions. So we also have usually a separate GitHub repo - maybe it's an API we're supporting, or an application, or something like that - the thing that's integrating our model. And then we use GitHub Actions, but other people use Jenkins, or Travis, or something for CI/CD. But what happens is we have GitHub Actions, which for those of you that don't know is like a -- it's integrated into GitHub, but it's a continuous integration, continuous delivery system, similar to Travis or Jenkins, or whatever... And so when we push a change into that repo, GitHub automatically runs a series of tests that we specify within GitHub Actions... So these are like unit tests for our Python code, and then deploys the updated version of the application. Let's say it's an API, it deploys an updated version of the API.

Now, what's interesting, I think, where this connects with machine learning, and the model bundle is like, if we update that API to use a new model, what I kind of recommend our team do - and we don't have it integrated everywhere, because, we have limited time, but in an ideal scenario, what we'd have is a sort of minimum functionality test for this updated model. So if it's a sentiment analysis model, I would have a series of like a table of tests that would say, you know, one sample is like, "This is a really great thing, and it's so awesome, and that should be rated as positive sentiment always." Regardless of what model I update, it should always get that right. And so that way, if I update a model and I point my API to the new model bundle, in CI/CD it'll run that minimum functionality tests against the functions that are calling my model. That way, if I accidentally pointed to a really bad model that can't even pass minimum functionality, then it fails the build, and it won't deploy with the new model. So it's almost a table-driven test that's used in like APIs and such, except it's really a test against the functionality of the model, versus the functionality of the actual application. Have you seen it approached in other ways? I'm always curious to kind of learn what people are doing in this respect.

**Chris Benson:** \[00:20:30.29\] So I'm gonna say nice things about what you're saying, and I'm gonna do this despite the fact that you're my co-host on this... So I would say this to anybody... No, I think that you have the benefit of having been a software developer as long as you've been a data scientist, and so you're able to see both sides of that. I think that's often absent, that perspective.

So what you've described - you've picked some specific technologies that you want to use to support CI/CD efforts, which are fine, and I think that there's a whole bunch of different options there that are all more or less equally good, with some pros and cons to each one, as normal... But you've integrated it so that you're not only testing the software, but you're testing your data by testing how that data is running through the model and inferencing. So that is a very, very cohesive system. Unfortunately, here's the bad news. I think that your approach is a little bit more of the exception than the rule in the broader industry out there. I've seen this at a number of organizations, where the skill sets of understanding that are still kept kind of in separate groups, separate departments, maybe even whole separate organizations... And I think the benefit of being working for a relatively small organization, not a giant Fortune 500 thing, is that you're able to keep everything close enough together and your expertise is able to intertwine to solve that well. And I think that that is a good guideline for others to look at.

If you ever find -- I know you have all this spare time on your hands, but should you ever find it, I think maybe actually publishing a little thing on that would be a useful tool for people to kind of see how you've approached it, other than just listening to the podcast here... Because you're kind of hitting -- you're hitting those software best practices, and you're hitting the data science best practices together, and treating the model as an artifact that needs to work for testing in that software deployment process and delivery. So anyway, I love what you're doing there.

**Daniel Whitenack:** Yeah. I think if there was a takeaway for people that might get them thinking -- like, you don't have to do things exactly that way, and I'm sure there's better ways to do it... But I think one thing I've learned over time is like, if your model is being used in software, and you can update your model without that software being retested in some way, there's like a huge risk and problem, right? Because you could just run another training run, and your model gets updated, and all of a sudden your software product breaks... But the software team, or the other people working on it - they're all transparent to them.

So that step, whatever it is - that could even be manual, right? Like, you don't update the model in one S3 bucket until you run the script to test it, and then you update it. Like, it could be manual in that way, if nothing else, right? But there needs to be some process there.

**Chris Benson:** Yeah, that can be brutally hard to debug, something like that... Because if you only have that insight -- going to your example, if you're the software team and you haven't made any changes, and yet now your deployed and delivered software has just broken and you don't have insight into the fact that the model changed, you can waste weeks of time trying to figure out what happened on that. So it's a huge productivity hit not to have that point of integration and to apply those best standards.

In the scheme of things, it's still complicated more so than it should be, but it's cheap in the sense that the things that you need to run and store and keep up with in that versioned manner is not hard today; that is a capability that anyone can afford, and to not have the discipline to do that can result in some real challenges that waste a lot of time there. So I'm with you on that. I think that having those integrated and having the discipline to do them together, and make sure that it runs at the end is pretty vital to moving as fast as we can.

**Break:** \[00:24:44.08\]

**Daniel Whitenack:** Well, Chris, I sort of went down the infrastructure rabbit hole, as I often do, and my team will tell you that I often go down that rabbit hole... But there is a lot going on else in the AI world that has sort of hit our desks over the past weeks... You forwarded something to me related to some of what you've been following in the aerospace kind of industry, or your own interest in piloting, and that sort of thing. Do you want to describe that a little bit?

**Chris Benson:** Yeah, I'd be happy to. I ran across something - Carnegie Mellon University, which is by any measure one of the top AI schools, often described as the top AI school in the world, definitely in that top half dozen, without question, released a paper on something that they had been doing in their robotics organization, which is entitled "AI pilot can navigate crowded airspace." And of course, this appealed to me both from the AI perspective, the fact that I am a pilot, and the fact that I work for an aerospace company. So it hit me on a bunch of fronts.

In this one, what they did was they put together a model and trained it, and had been testing it in simulation, that enables an autonomous aircraft to navigate crowded airspace. And for those who don't fly as pilots, airspace around airports gets very crowded, and you really have to work hard to maintain separation and keep things safe, and such. So this is a non-trivial problem. People that don't pilot will look up and go, "Well, you've got the whole sky there. How bad can it be?" But you're also in fast-moving vehicles, and you're all moving in the same patterns, so you can have a problem very quickly.

So this is a pretty important challenge to overcome, and it's one that we know that the industry is pushing for. So I will say, kind of obliquely, in the military space, where you're not necessarily in air patterns and stuff, we're doing autonomous stuff, as is reported in the general news, all the time, in terms of aircraft. And I think that's fairly well understood. In the civilian space though, if you'll imagine in the future being on an autonomous airliner, and you and 200 of your best friends are flying around, and you have AI models that are driving this - it's not as hard to move between busier spaces. As you're moving across maybe the countryside or something, you're kind of out there by yourself, and there's not as much to do. But on the start of that journey and on the end of that journey, there are a lot of other aircraft in close proximity to you, so the ability to do this is pretty important.

\[00:27:51.23\] They say that this model can safely avoid collisions, predict the intent of other aircraft, track those aircraft and coordinate with those aircraft's actions, communicate over the radio, it uses natural language processing to do that... It has a vision system that uses six cameras to visually track... And one other distinction - in general with flying there are two kind of systems for flying. One is instrument flight rules, which is what you would think of with airliners, and one is kind of what us private pilots (the little guys, so to speak) do, which is visual flight rules. And you tend to have visual flight rules lower down to the ground.

And so this system - we've had automatic flight control systems in airliners for decades that fly, but those tend to be high up in the sky, and you're kind of alone traffic-wise. This is designed to do visual. It can work with instruments, it can work with radios, it can work with cameras to do the visual stuff and make all the decision-making in real time, right there, to keep everybody in the sky safe. So it's a pretty cool problem to solve, and it's one that eventually -- I know people shudder when I say this, but I think that it is not so far out that all of us will be getting on airliners that are almost entirely automated. They might have a human in the cockpit because it makes us feel better, but eventually that just won't be really needed... And so this is one of those big steps toward trying to do that. And they're combining, going back to a theme that we've been talking about lately - they are combining natural language processing models with visual processing models, they're integrating those, and they're being able to use that system across multiple domains to affect a real-world solution here. So I think this is very much in line with the kinds of innovations that we've been looking at over this past year.

**Daniel Whitenack:** Yeah, so I have a couple of follow-up questions on this, which is really interesting. One is I just want to maybe get your perspective, since you're more plugged into this space and have interest in the area... I Know that it's been talked about for quite a while that the sort of short or last mile kind of trips, like in a city, in a large city, you could have like air taxis, which are basically like humans in a big drone, and flying around the city. My understanding is any reasonable person would say, "Well, there needs to be computer systems within that, that would coordinate and manage the safety of all the routes." If there's a bunch of things flying around in the air, it gets very complicated in a crowded space. So maybe this gets us closer to that... Do you have any thoughts?

**Chris Benson:** It does. So I'll comment -- I'll both answer your question and I'll make a reference that not even you know about me, not just the listeners... The specific issue there is you're talking about massively scaling up the number of platforms, as I would say in my industry, that are in that space, which is my specialty. If you were to say, instead of having ten things in a given closed space - it could be airspace, it could be on the ground - what if there were 10,000 in the same space? Maybe not all big, but maybe many are very small, autonomous... How do you manage that? That's specifically where my current focus and expertise lies.

**Daniel Whitenack:** Oh, cool.

**Chris Benson:** And so this is a control system for aircraft that can enable things like autonomous taxis, and package delivery, and all these other things... It doesn't solve the whole problem. It kind of solves the how do you make decisions from one platform; it doesn't necessarily solve all the integration things when you have a massively scaled situation there. But it's an important step. It's really, really crucial to enable this future of civil aviation, which includes all of these low-flying drones, package deliveries... Kind of like when we look at a Hollywood movie, these futuristic science fiction movies, maybe Star Wars, and all the city is just full of flying things everywhere, at every level. We're heading that way, but we need to get some of these technologies in place, and this is a key, crucial Lego in that pile of Legos to build that.

**Daniel Whitenack:** \[00:32:12.27\] Yeah. My second follow-up question to that, which is - it's funny that this came up today when we're chatting, because... So I always listen to podcasts when I'm in the shower, which is a weird way to start the subject... But one of the ones I really like is DarkNet Diaries. I love DarkNet Diaries, and just the stories there... But I listened to one this morning, it was actually from a while ago with a guy named Sammy... And he created this sort of proof of concept, which you can look at on GitHub, where -- it's called SkyJack, and essentially what he showed at the time... This is a while ago, I'm sure things have gotten better now, but he showed that he could put a drone up in the air with an antenna on it and a Raspberry Pi, and basically wherever he would fly it, he would hijack the other drones around, because the signals, he would intercept, and he could actually take control of them.

So it's one of these things, like, anything that's connected is hackable, right? And so also as you kind of increase the number of things in an area... I think certain people might think, "Oh, that's dangerous, because a computer is automating the flying." I think the dangerous part is not the computers automating the flying, but humans hacking into the computers automating the flying maybe. So I don't know, from your perspective, how security impacts these sorts of systems...

**Chris Benson:** Hugely...

**Daniel Whitenack:** Yeah. As you automate things in this area, it's -- the computer can obviously do... Well, maybe not obviously, but I buy into the fact that a computer can do a better job at this sort of flight control than a human. But it makes it sort of hackable as well. Right?

**Chris Benson:** It does. And if anyone doubts that computer and model together are better at this point, you can google "DARPA AlphaDogfight." A couple of years ago there was a public -- it's on YouTube, there was a public demo where... And we talked about this briefly on the show before, where they had automated -- a bunch of companies brought their autopilots, they put them on an F16 simulator, and they competed against each other, and then they had to compete against an Air Force instructor. And that AirForce instructor was the equivalent of what we would think of as a Navy Top Gun instructor. It was a weapons school instructor. And the top one that went against the human absolutely demolished him in a dogfight. I mean, demolished him, five times in a row. It was just stunning to watch.

And so yes, computers can currently do this better than humans can, even if you're the best human in the world. So that's already a done deal, and it's just being improved upon sense. So when people are worried about computers flying these things, I would much rather -- I'm that one person who would much rather for this technology to be flying the airliner I'm in than the human, because I know what the difference is in capability.

So it doesn't solve everything, and it doesn't solve what happens at massive scale when you're struggling to get to handle all of the things in the airspace together, but it's pretty crucial. And I think your point about the cybersecurity - cybersecurity is huge when it comes to aviation and autopiloting, because it's a natural thing to hack. In my space, which is defense-oriented, you would assume that your adversary is always going to actively try to do exactly that. So it's just built into the equation; we're automatically handling that as we solution for it. And that will obviously roll out into the civilian space as well, and air taxis, and package delivery. All of that has to have that cybersecurity capability.

**Daniel Whitenack:** \[00:36:03.04\] Super-interesting. I'm glad we went down that that rabbit hole...

**Chris Benson:** It's fun. I love talking about that.

**Daniel Whitenack:** Yeah. One thing I wanted to highlight maybe just somewhat quickly before we get on to learning resources is I took a look recently, it popped up in my Twitter feed, one of the things, but I looked through the whole set of demos, and I would recommend people go and check out some of the NVIDIA AI demos that are coming out. We'll link to that in our show notes. I was kind of -- like, I don't know if I just hadn't looked at it in a while, but I looked there and I was like, "Oh, wow", and then "Oh, wow...!" and then another "Oh, wow!" There were all sorts of things I wasn't -- I mean, I sort of peripherally knew were going on, but really powerful kind of demos... One being this way of taking sketches and turning them into photorealistic images. This is kind of related to some of the image stuff that we've been seeing recently.

Another really cool one I thought was this vid-to-vid cameo thing, which you could sort of synthesize a talking head based on an image of yourself that you could use in, for example, like Zoom calls. So you could just have like your talking head synthesized based on imagery, versus like your actual video on the Zoom call... Which I thought was really, really interesting, and something I kind of want to try.

**Chris Benson:** No, I agree with you. I'm so glad that this podcast is audio-only, because if it wasn't, we would absolutely, definitely need to implement that to make us presentable. We have faces that are made for radio, so to speak, or podcasting in this case...

But yeah, we're already starting to see that. I mean, using Zoom - a lot of folks are using Zoom and other platforms like that at work, and I always have alterations that I'm making to make it more interesting, and stuff. And some of them actually do do the facial fixes in real time... So yeah, that sounds like something that I definitely need. My wife would, I'm sure. She's always telling me, "Oh, gosh, you need to look better than that."

**Daniel Whitenack:** \[laughs\] No comment from my end. Well, let's maybe hit a few learning resources as we close out here. I think going straight off of the NVIDIA stuff, which is mostly vision and 3d things, I wanted to highlight this paper that I saw trending on Papers With Code... It's a survey paper, so it's a little bit maybe more approachable in some ways. 3D Vision with Transformers: A Survey. This is from Jean Lahoud et all, and they go through and talk about all of these sort of 3D representations, and using transformers on 3D data for vision... It's really interesting, and if you're kind of wanting to get an overall picture of some of the things going on in this space with 3D data, I think that's a really interesting place to get some of that information, all in one sort of shot.

The other thing I was going to mention, which is not related to vision, but back in my sort of world of NLP - there's going to be a natural language processing with transformers course. It's going to be in September through October of 2023, and there's some people from Hugging Face that are teaching that. It looks pretty awesome. It's like live teaching sort of thing. So yeah, I would definitely recommend check that out if you're interested. It is paid, but if you're interested in that sort of paid, live learning opportunity, then it seems like a really good one to learn some of the latest stuff.

**Chris Benson:** Yeah, good people teaching it there, in terms of - if you're going to spend money on it, spending it for people that are at the top of their field.

**Daniel Whitenack:** That are legit. Yeah. Exactly. Cool, Chris. Well, that's all I had for today... I enjoyed the various rabbit holes we went down, and learned a little bit about aviation along the way... So yeah, I appreciate the conversation.

**Chris Benson:** Yeah, absolutely. Keep flying high, Daniel. I'll talk to you next week.

**Daniel Whitenack:** Alright. Bye-bye.

**Chris Benson:** Bye-bye.