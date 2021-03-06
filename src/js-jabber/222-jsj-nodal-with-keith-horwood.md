---
layout: layouts/post.njk
title: >
  222 JSJ Nodal with Keith Horwood
date: 2016-07-27 09:00:37
episode_number: 222
duration: 56:47
audio_url: https://media.devchat.tv/js-jabber/JSJ222Nodal.mp3
podcast: js-jabber
tags:
  - js_jabber
  - podcast
---

02:35 - Keith Horwood Introduction

- [Twitter](https://twitter.com/keithwhor)
- [GitHub](https://github.com/keithwhor)
- [Blog](https://www.keithwhor.com/)
- [Polybit](https://polybit.com/)
  02:50 - [Nodal](https://www.nodaljs.com/) | [nodal](https://github.com/keithwhor/nodal)
- [The LAMP Stack](https://www.turnkeylinux.org/lampstack)
- [Node.js](https://nodejs.org/en/)
- [Django](https://www.djangoproject.com/)
- [Rails](https://rubyonrails.org/)
  05:41 - Frameworks07:56 - Async Flow; Callback Execution
- [Brian LeRoux](https://brian.io/)
  10:29 - Nodal Use Cases13:11 - [GraphQL](https://graphql.org/)15:07 - [PostgreSQL](https://www.postgresql.org/)17:56 - Developer Evolution
- [github.com/poly/dotcom](https://github.com/poly/dotcom)
  24:05 - Scheduled Tasks and Migrations
- [Sidekiq](https://sidekiq.org/)
  28:57 - ORM Flexibility33:14 - API Payloads35:24 - The ORM40:37 - Testing43:10 - 1.0?45:18 - Getting Started&nbsp;Picks
- [The 2016 UtahJS Conference](https://conf.utahjs.com/) (Dave)
- [Writing good code: how to reduce the cognitive load of your code](https://chrismm.com/blog/how-to-reduce-the-cognitive-load-of-your-code/) (Aimee)
- [Natural Calm](https://naturalvitality.com/natural-calm/) (Aimee)
- Unplugging from technology (Chuck)
- [#CodeNewbie](https://twitter.com/hashtag/codenewbie) (Chuck)
- [Angular Remote Conf](https://allremoteconfs.com/angular-2016) (Chuck)
- [React Remote Conf](https://allremoteconfs.com/react-2016) (Chuck)
- [Rails Remote Conf](https://allremoteconfs.com/rails-2016) (Chuck)
- [All Remote Confs](https://allremoteconfs.com/) (Chuck)
- [React, IoT, Bots, APIs — Why Web Development Needs a Change](https://medium.com/@keithwhor/react-iot-bots-apis-why-web-development-needs-a-change-299930cec3c6#.x6e4mcfnn) (Keith)
- [fortran-machine](https://github.com/mapmeld/fortran-machine) (Keith)

### Transcript

**DAVE:&nbsp;** They haven't been able to edit out the nasally portion of my voice yet though, so I can't help you there.

**_[This episode is sponsored by Front End Masters. They have a terrific lineup of live courses you can attend either online or in person. They also have a terrific backlog of courses you can watch including JavaScript the Good Parts, Build Web Applications with Node.js, AngularJS In-Depth, and Advanced JavaScript. You can go check them out at FrontEndMasters.com.]_**

**_[This episode is sponsored by Hired.com. Every week on Hired, they run an auction where over a thousand tech companies in San Francisco, New York, and L.A. bid on JavaScript developers, providing them with salary and equity upfront. The average JavaScript developer gets an average of 5 to 15 introductory offers and an average salary offer of $130,000 a year. Users can either accept an offer and go right into interviewing with the company or deny them without any continuing obligations. It’s totally free for users. And when you’re hired, they also give you a $1,000 bonus as a thank you for using them. But if you use the JavaScript Jabber link, you’ll get a $2,000 bonus instead. Finally, if you’re not looking for a job and know someone who is, you can refer them to Hired and get a $1,337 bonus if they accept a job. Go sign up at Hired.com/JavaScriptJabber.]_**

**_[Let's face it. Bookkeeping is hard and it's not really what you're good at anyway. Bench.co is the online bookkeeping service that pairs you with a team of dedicated bookkeepers who use simple, elegant software to do your bookkeeping for you. Check it out at Bench.co/JavaScriptJabber for 20% off today. They focus on what matters most and that's why they're there. Once again that's Bench.co/JavaScriptJabber.]_**

**_[This episode is sponsored by Rangle.io. Rangle have been working with Angular 2 for a long time, and they are now putting together an 8-hour, 2-day course designed to help Angular developers, learn how to write apps in Angular 2. If you're looking to level-up your JavaScript and Angular 2 skills, go to Rangle.io/Training and click on the link for Angular 2 Training. If you're looking for other training in React or JavaScript, they also have that available at Rangle.io/Training.]_**

**CHUCK:&nbsp;** Hey, everybody, and welcome to Episode 222 of the JavaScript Jabber Show. This week on our panel, we have Aimee Knight.

**AIMEE:&nbsp;** Hello!

**CHUCK:&nbsp;** Dave Smith.

**DAVE:&nbsp;** Greetings.

**CHUCK:&nbsp;** I'm Charles Max Wood from DevChat.tv. Quick shout out about Angular Remote Conf and React Remote Conf coming up in the Fall. We also have a special guest this week, and that is Keith Horwood.

**KEITH:&nbsp;** Hey, how is it going?

**CHUCK:&nbsp;** Do you want to give us a brief introduction?

**KEITH:&nbsp;** Sure. I'm the lead author of a project called Nodal, which is a Node.js MVC Framework for very easily creating API services.

**CHUCK:&nbsp;** Awesome. Now that's pretty concise, I'm assuming that there's a bit to it. When looking at it, and Aimee pointed this out to me, and then you know, I went looked at it again because I just kind of skimmed over it initially, is that it looks a lot like Rails.

**KEITH:&nbsp;** Yeah. The story behind Nodal is a pretty long one. Well, I think, I can shorten it down here. But I've been a developer who's worked with a lot of different language and a lot of different frameworks. I really started web developments with the LAMP stack, which I think is probably pretty familiar to most devs in the space. From the LAMP stack, I migrated originally to Django, and then, spent a bit of time working with Rails.

Now, once you start working with MVC Frameworks, you just had this huge boost in productivity that you don't really want to give up at any point moving forward. The problem was, is that like I really, really like JavaScripts. From the perspective of just managing cognitive overhead, I suppose, decision making, I prefer to just be able to work in like one language on the front and the back-end, and I think that's pretty common now in the developer community. We've seen a bunch of tools evolving around this. Node.js has obviously opened up that space.

The problem is coming from like Django and Rails to Nodes, there wasn't anything as good as Django or Rails in the Node space. There are a couple of frameworks, I mean, sales had boost in popularity a few years ago, but it was based on like old JavaScript known as ES5 syntax, lots of boilerplate, dealing with prototypes, weird language constructs that just kind of felt unfamiliar from somebody who's built back-ends in Django and Rails. Coming from that perspective, when the Node.js-io.js fork happens which was, I don’t know, I think early last year, early 2015, maybe February or March. There was a pretty awesome opportunity enough that the newest versions of the V8 engine that the Node was running on supported modern JavaScript ES6 syntax, which were things like class syntax, for actually defining classes in a way that developers coming from other frameworks or languages are kind of more used to it. It's like this idiomatic way to set up classical inheritance on object-oriented programming.

I noticed the opportunity there to bring the design patterns that were really awesome from Rails and Django, and bring them into the Node space. So once that io.js fork happened, I started- I don't even like throwing together frameworks in JavaScript - reinventing the wheel over and over and over again, building back ends in Node, layered on top of the Express and all of this stuff. So I said, "For once and for all, now that we have class syntax in here, I'm going to bring the design patterns that developers are used to from other big MVC players and bring it to the Node space."

**DAVE:&nbsp;** I'm just trying to think of a joke here. You mention how you're kind of hobbyist building JavaScript frameworks in your spare time, and I thought you and every other JavaScript developers --

**[Laughter]**

**KEITH:&nbsp;** Oh, my gosh, yes. For sure, that's something interesting in any about the JavaScript space, right? Especially, the Node space, I think, it's pretty common or like Node was kind of founded on the UNIX principles of like each piece of software, each module should do like one thing really, really well. So, as the Node.js ecosystem exploded, everyone started making this small modules that did one thing really well. It was very effective from like a barebone standpoint.

If I just want to build a program that does something, I'm going to go on npm so I'm going to look through npm packages and I'm going to figure out exactly what I need. The problem is that in web development in general, when you're building like a web server, there's a lot of pieces of common and shared functionality that people recreate different small packages for and all of the sudden, it becomes like ordering off of, I don't know, like a dinner menu at a fast food restaurant with like too many options, and you lose productivity because instead of being like, "Oh, I have all these options. I can create whatever I want."

Now, it's kind of like, "Wait, I don't really know what to choose what's the best and teams especially, working on JavaScript products," because developers are all opinionated. I'm opinionated. I don't think it will work with an engineer who doesn't really have some sort of opinion to how things should get built, and that's kind of what the value that frameworks provides is they start curating some sort of common tool set for doing the same types of operations over and over. And in the case of MVC frameworks, it's really creating web servers.

I think, that's kind of unique in the Node space as people kind of getting pushback against frameworks, really since Node kind of erupted on to the scene, but I think everyone now, as more and more developers adopt it, people like, "No, you know what? Okay, let's just get the stuff that we want to get out of the way done really, really quickly so we can actually focus on the cool stuff and start playing around with, I don't know, machine learning packages and things like that and get the web server stuff - the boring stuff out of the way."

**AIMEE:&nbsp;** I have a question. If I am reading your issues crackly, this is like the question that immediately came to my mind because having done a little bit of Rails before I jump over the JavaScript, this project looks really interesting to get newer developers be able to create something quickly but there's still like one big difference between Ruby and JavaScript and that being like asynchronous flow, and that's kind of when you're new to programming, it can be a little bit difficult to wrap your mind around.

But the issue someone brought up using promises instead of callbacks, and as someone who's been programming a little while now, like I definitely prefer promises over callbacks. So, I'm curious. It looks like you have decided to hold off on promises and you're preferring that people still use callbacks and that you're hoping for a single way to make it to the specs so that you could use that in the future.

**KEITH:&nbsp;** Yeah, I'm actually on offense about that one right now. I've read a lot of what's developer, Brian LeRoux has written. He's the main author, and I have talked to him a little bit. He's the main author of Apache Cordova there - one of the lead authors of that projects. His opinion when him and I were discussing it, his opinion on this space that I have a tendency to agree with, is that promises introduce extra complexity into application by introducing state.

The fact that you can assign a promise to a variable, and then it either has a state of like has executed, has not executed, has failed, has not failed introduces extra complexity in your program. Whereas, callbacks are for control flow management only so there's less chance. It's kind of like giving developers enough rope to kind of hang themselves with.

Yes, even though, newbie developers especially didn't get lost in this spaghetti code world with tons of nested callbacks, it's still a way to manage control flow without ever having to worry about the state of callback execution. That's what I think kind of actually simplifies that control flow process overall, and why I prefer it as a design pattern at this point. I know promises- I'm kind of stray a little bit away from the front-end over probably the last eighteen months. But I know promises have just taken over in terms of how developers are writing code and designing.

It might be just that I haven't spent enough time really figuring out what those design patterns but I still don't like that idea of just having that state behind the scenes that you have to potentially could shoot yourself in the foot.

**AIMEE:&nbsp;** Interesting.

**DAVE:&nbsp;** What would I build with Nodal?

**KEITH:&nbsp;** Nodal is super-focused on building API services in Node. We don't have any like template functionality, any support for providing static assets. We used to in earlier versions of Nodal but we kind of decided to take a direction of just providing functionality for API services. The insight there being, that's kind of how developers all across the industry are really thinking about building tools now. I mean, one development come a long way in a very short period of time.

When Rails kind of started owning the scene there, in the mid-2000s, people were treating the web browser as if it was a client. I mean, it is. A web browser is a client. But your back-end server was only focused with really providing you logical of that stuff, templates, etcetera to the web browser.

Now, we've kind of had a shift in the way people think about developing applications that the server should be completely decoupled from your client phasing rendering logic. I mean, we've seen the rise of single page applications, especially in the past like three to four years with Angular, with React, with whatever. This single page applications don't necessarily- I mean, some people are doing stuff with server-side rendering but don't actually require server-side rendering of any sort of HTML or user interface logic whatsoever. So your API could be just completely focused on business logic, and so people are building applications now.

With that insight, I don't want to create, like a catch all solution that just lets you do everything. Though, that's valuable for prototyping, I suppose. It’s not really how people are building anymore. The added benefits of working with that API first layer in building that API is your central kind of block your application is that what's going to be doing your service dispatch to third party services, if you're like, say, connecting to something like API.ai for some natural language processing or something like that. You're going to offer that to a third party service, anyway, and you also have the ability to support any type of client without worrying about the client type.

So a mobile app can connect to an API like an IoT device - Internet of Things device - can connect to an API. You're not worried about rendering logic, or template logic, or whatsoever in those cases. I want to provide a general solution for building that system type of an API, knowing there's- I mean, there's three things that developers really needs to get a back-end API up and running. They obviously need their business logic, which is what Nodal provides. They need to connect to a database layer which Nodal has its object relational manager for, and they need a key value store ideally just for that faster storage of states which we'll be getting into in the next few iterations of Nodal.

**AIMEE:&nbsp;** One other interesting thing that I was reading about is that it looks like you're working on or you plan to start supporting GraphQL with Nodal.

**KEITH:&nbsp;** Yeah. It kind of just started out as like an experiment, as like a what-if. When you're building an ORM, I kind of wanted to build- I mean, the ORM syntax in Nodal is completely borrowed from Django. Django's ORM is fantastic. It’s made working with databases, so easy, it was great. I kind of borrowed a lot of patterns from that.

But in order to support everything that Django's ORM does, you need to be able to simply walk through the relationship graph or relationship tree of how all of your models, like your data models, are related to one another. You could have a user that plays a sports and then, from that user object, you want to be able to know what sport they play. Maybe that sport has specific games associated with it throughout the year. You want to be able to associate that to user. You have to traverse this relationship tree, and I realized like, I'm literally just doing graph traversal here.

This is like, if I can find an effective way to do this graph traversal, it lends itself really easily to this GraphQL layer. That's what I did. I have extracted the ORMs level so it actually just does a graph traversal between all your model relationships, and then I just created a mapping layer that's a one-to-one maps that do GraphQL query. So you can accept a GraphQL.

We have a little bit modified syntax. The standard for GraphQL is still early so we kind of accept our version of GraphQL which maps to our ORM language essentially, our dimensions of the language for ORM, which then runs accordingly behind the scenes on a relational database. So I think that's what's really cool is that we're not using like Mongo, where we're actually using a relational database. We're trying to keep it as normalized as possible, and still be able to run GraphQL query on it.

**AIMEE:&nbsp;** You're using Postgres, right? So what went on to the decision for that?

**KEITH:&nbsp;** Postgres was --

**AIMEE:&nbsp;** -- very Rails-like.

**KEITH:&nbsp;** Yeah, I mean, Postgres was just a familiarity decision to be honest. The first database I have ever really truly worked with was MySQL with the LAMP stack. I love MySQL. It's great. Postgres, I've just been working with for a number of years, and it does a lot of things really, really well. It does support JSON B. You can still provide Postgres with unstructured data, like you would with something like Mongo, and you can still query against unstructured data so you don't lose that ability.

I just like Postgres overall. It kind of a familiarity decision, and then, just picking what works. So as kind of like an aside or related to that, I'm very opinionated about frameworks and the value that they adds. We see a lot of frameworks in the front-end lands, start offering things like, "Oh, okay, you can write your front-end application in- You can use new ES6 syntax with Babel or you can use ES5 or you can use TypeScript."

In fact, I actually think this is a really huge problem with Angular, is that Angular let you do anything like almost any way you want it. So Angular wasn't really a framework per se. At least the last version of Angular - the Angular 1.X - wasn't really a framework in the true sense because, I tend to be a purist here, and that frameworks make decisions for you. That's the biggest value add.

the biggest value add is that when you're in a team - an engineering team, before I was working on my current startup, I was a lead engineer to a startup called Storefront, the biggest value for an engineering team is having decision is made for you so you don't have to get in a group together and say, "Hey guys, what technologies are we going to use? What stack are we going to use? Why is this important?" You're going to waste tons of engineering cycles just deciding on that.

If frameworks make those decisions for you, your current developers don't have to worry about that overhead, and as you on board new developers, they don't have to start thinking about, "Oh, my gosh. What's the right way to do something here," because they already have standard best practices for that framework. I think, the more options that you give developers in a certain context with frameworks, the value of the framework actually continues to decrease.

We see a lot of generalist technology solutions that actually lose value by not being prescriptive enough and have a hard time capturing market share just because of that. I'm pretty opinionated in that space, so Postgres was a decision that was like, "Hey, you know, I noticed TBMS. I like it, developers are trusted, this is the decision we're going with and we're going to stick with it."

**AIMEE:&nbsp;** That's kind of [inaudible] like I agree with a lot of that, and I feel like, as a newer developer, that's really important. But you know, as you get better and more advanced and then, especially, I feel like with senior developer that kind of probably takes away a little bit of their fun and the challenge of having to make some of those decisions. So, kind of interesting.

**KEITH:&nbsp;** Yeah. I think, there's a general developer evolution that all of us tend to go through. As junior developers, we kind of want to get things built, and don't really necessarily understand how everything's working behind the scenes. So we go through this phase of like, "Okay, let's just get something done. Let's use the solution that's best practices. Let's get it out of the way so I can actually build this application."

Now, as you're doing that, you're from technical [inaudible], you're like, "Okay, I didn't do this properly. I didn't listen with the best practices," so a few of us get chips on our shoulders and that's not necessarily because the tool we were using was wrong or bad. It might just because we didn't know enough about how to use the tool or the prescriptive best practices to work with it effectively. In fact, when I first dealt with Rails, I ran into this problem immediately, and I just started building in Rails because that's what I do. I didn't follow the Rails best practices and read all the documentation and whatnot so I started building a lot of pretty cumbersome stuff in Rails, and I had another developer come to me- I mean, I was a season JavaScript developer at this point, not too much Rails experience, developer come to me and be like, "You just didn't know all of these design patterns that Rails is going to encourage because you didn't read the docs and you just hack it out."

One of my frustration, a lot of things that was created was just because I didn't know what I didn't know, and so developers go through to this phase. The junior developer, I mean, I accept this prescriptive solution because it get something done. You go to this intermediate phase, while all of a sudden it's like, "Oh, my gosh. I'm so frustrated. There's so much technical here. I just want to recreate everything from scratch," and then, I think we kind of start developing towards this Zen stage of like, "I was a little bit hard headed. The value here that was added was actually a great amount of value, and now we're just going to stick with that. We're going to go back to that prescriptive solution because I want to actually focus on making larger systems - more complex systems. I want to work with cool things, like machine learning that sort of thing."

**CHUCK:&nbsp;** Yeah, I definitely see that. There is a lot of pushback that's going on now, though, with Ruby community with regard to Rails because it takes on so much within the context of the framework that a lot of times, people have a hard time figuring out what all the pieces are, what's moving where, and what's going on with what. So it's almost got this feature bloat problem now that people get upset about. Whereas other people say, "Well, it does all these things for me, and it solves all these problems for me," and so they're still excited about it.

It seems like there's a balance to be reached so to speak, especially when it comes to particular people with particular problems. So how do you strike that balance? How do you figure out how much to prescribe, and maybe where you may have stepped over the line for certain problems that certain developers are going to try and solve?

**KEITH:&nbsp;** You always run into this problem in development. It becomes a much larger problem. The larger the community, that's contributing to an open source project, so likely with Nodal, I've still be the main author, and to this point, I've been able to stray away from those problems with complexity. But I think it comes down to thinking about systems and use cases, and what people are actually going to be building. At what point do you say, "Okay, I'm going to add this to this framework because I think developers want it, a bunch of people are asking for it," and for you to say like, this actually belongs to like a different problem class. You're solving something completely different here.

An example that I would make- it's kind of like what you get and see in the definition, so use a concrete example. With Nodal specifically focusing on API servers, there was a lot of code that we actually just got to completely drop from the Nodal code base. That had to do with templates, initializations, static asset compilation, like JavaScript's Sass, that sort of stuff. We got to cut it from the project entirely. So we started accumulating this technical documentation bloat for all these features. I was like, "What's actually the common use case for Nodal? What's the actual cool things that people are doing with it," and I was like, "You know what? It's really focused on this data manipulation, this ORM, this GraphQL type stuff," and if people want to start serving static assets, then for end developers, I already know their workflows for static asset compilation. People are already using gulp and grunt. I think there's complexity in that space too that can be reduced, but it's not going to be a focus for Nodal.

Another good example would be, we got really asked early on like, "Okay, I want to use socket.io with Nodal." I put my foot down pretty hard there, and said, "Look, you can try if you want to, but it's not going to work the way you expected to." Nodal is focused on just being a stateless API solution. Just essentially for like the skeleton of your application for getting those incoming HTTP requests, and doing service dispatch and communicating with your database, and doing some validation of business logic on the inside. But it follows that 'one request, one response' model and it's very opinionated about that.

So when somebody comes in and asks for like sockets, well, I could say, like actually, "You know what? A lot of people do want to build real time systems. Let's have Nodal support that," but the way I kind of view this, and the kind of the future of web development as a whole is in providing prescriptive solutions for systems. So the [inaudible] developer that wants to bring in real-time and say, "You know what? Nodal doesn't do real time but there's another solution that you're going to want to spin up that's-super specialized for real-time that you can integrate here with Nodal." Or somebody says, "I want to a static server just to compile templates and all that stuff."

In which case, I would say, "Look at this project called DotCom, which is at GitHub Polly/DotCom. No documentation right now but pretty much all the templating and compilation logic at [inaudible] compilation logic that was originally in Nodal, we offloaded it to a different project and said, "This is a different system that you're dealing with," and it has different deployment requirements, it has different scaling requirements so think about this like at a different product track. You're building like a static branding server, or whatever. You're building like an API server. If you're building an API server, use Nodal.

That's the way I think, about this. The way I think you can avoid that complexity within a single project is by actually just thinking these are different products completely.

**DAVE:&nbsp;** So far, we've talked about database integration with the Nodal ORM, and talked about API like route dispatching URL - dispatcher. But it looks like Nodal has a whole bunch of other services, too, like schedule tasks, and migrations and stuff like that. Do you want to talk about those?

**KEITH:&nbsp;** Sure. As of Nodal 0.11, we haven't worked on the scheduler much. We haven't had a lot of developers playing with Nodal that have been using the scheduler. A scheduler is a very important piece of development stack in general. But I have some internal questions about where that's going to go.

But in terms of database migrations, that's a core part, like an API lair. If you're saying that a stateless API system is going to have like three parts to it, like I mentioned, that it's going to have like that routing and that actually [inaudible] layer. It's going to do service dispatch, with just this third party modules and stuff. But it's also going to save state in a database or [inaudible] store, then you need to be able to manage that database which is where migrations are just super useful.

I think, Rails did migrations right. I think it's the easiest to reason about so standing on the shoulders of giants, I don't see a migration system that pretty much matches Rails. Any developer coming from Rails will be familiar with the way the migrations worked in Nodal. That was the opinion. Now, the schedule tasks, I still have questions about where that's going to go, and how that's going to evolve as part of Nodal in general.

**DAVE:&nbsp;** Are you planning to provide a background task execution system similar to Ruby's, I think, it's called Sidekiq or Python Celery Project.

**KEITH:&nbsp;** Yeah, I think, the last production environment I was working on at Storefront, we use Sidekiq exclusively for that. That was the basis for the scheduler, for running those background task. From a larger systems design standpoint, I'm still trying to figure out exactly where that fits in, and how I'm going to manage that. The scheduler will work if you're spinning up your own development environments. But that API is definitely not stabilized right now in Nodal so we're going to see that evolve over the next couple of months for sure.

**CHUCK:&nbsp;** I have to say, I definitely love Sidekiq and some of the other tools that are built around those ideas. Very handy.

**KEITH:&nbsp;** Yeah, there's a lot of like really low-hanging fruit, things developers have to do like all of the times that will require with like maintaining data consistency, running tasks. What's interesting about Nodes is just because of the asynchronous nature. You can do some cool things just with API, like in the context of an API request, that you wouldn't normally be able to do with Rails like what would Sidekiq for, as you can schedule an asynchronous task.

These are something and then, you need to send like an HTTP request because it's going to be hanging in the Rails environment. It's going to hold up that process in the thread. You normally just offload that to Sidekiq. But in the context of Nodal, because we're running Nodes, you consented asynchronous request off from your API controller. Actually terminate the API request for the user but still have that go beyond the scenes. That's just because the asynchronous non-blocking aspect of Node.js. That's kind of cool in that space. Solves that problem a little bit.

**DAVE:&nbsp;** Yeah, I've often wondered about that. I have not a back-end Node developer. I've only done Python on the back-end but if you do that, it's kind of an unsafe situation where you have a web server that you can't take down or can't take out of service because you have an unknown number of asynchronous requests that are just floating out there in memory somewhere.

**KEITH:&nbsp;** Perhaps. But I'm really not too worried about that. The way that we're actually approaching the development of Nodal is we're kind of heading towards the microservices architecture standpoint, and that's why we're very focused on keeping nodal stateless. Like not supporting socket requests because the idea of infrastructure and architecture behind the scenes is that with modern day infrastructural solutions, especially with stateless API requests, and in the microservices type architecture, there's not going to be a specific server that your application is running on.

A micro instance could have been spun up in one hundred milliseconds instantly that serves your request, or it could be one that's been longstanding for like, I don't know, an hour or two. You don't know what's going to be handling this request. This is why you don't maintain state within the JavaScript application, and this is kind of what Nodal is heading towards with these super-opinionated but being stateless.

If you do have a hanging API request in that context, then that micro container, or whatever respond up to handle that request will shut down, but you have an entire fleet of potential servers behind the scenes. So I'm really not too worried about that space with the way infrastructure is going and the way we're thinking about providing solutions there for developers.

**CHUCK:&nbsp;** We've talked about sort of the different aspects of what's included, but could you get some flexibility on the ORM because I know that, at least in Rails, a lot of people like to use something like Mongo or get MongoDB or other things. With that, it also occurs to me that you could also do something with it if the C and the controller part and aspect of this isn't that opinionated, and you could find a way to bolt on some layout stuff that you couldn't set an ORM for some kind of like local storage, and then run it on the front-end as well.

**KEITH:&nbsp;** Sorry, can you go to a little bit more detail of what you mean at the end there?

**CHUCK:&nbsp;** Well, first of all, there were two questions there. The first was basically, other databases or other ORMs, are you looking at making it modular so that you can swap them out?

**KEITH:&nbsp;** Not at this point. That's the argument I was making earlier about the value of frameworks. Lots of developers have opinions about the types of technology they want to work with, what they want to use, what they want their stack to look like, and that has a tendency to be in this middle phase like, "I'm figuring everything out. I don't like the technical that's been accrued in the past. This is what I saw that works here so why doesn't this prescriptive solution do it my way. I'm going to request this."

But I also think you start very rapidly losing the value of the framework when you start modularizing components like that because that - number one value add. The value prop for a framework is minimizing cognitive overhead and allowing teams to execute quickly, while still being maintainable, providing a common language or whatever.

The second is providing more and more options. You start also opening up more and more question marks. Now, with the amount of community members that you're going to make happy because they got the option that they wanted, you're also going to collectively just introduce these potential bottlenecks for tons of other developers that are completely okay which is like, "No, this is the solution I trusted. I'm okay with this." So it's a slippery slope.

The way that we've written the ORM is actually makes it extensible to work with any SQL DBMS, but at this point, it's not a focused provide modularity there. We'll be examining that for sure in the future, but it's not a top priority right now at this point.

**CHUCK:&nbsp;** That makes sense.

**KEITH:&nbsp;** Yeah, I'm sorry, the second question was about the- you're mentioning something about templates --

**CHUCK:&nbsp;** More along the lines of what it would take to make it into a front-end framework but we would have to make it modular in that way in order to work around some of the other issues that are out there for the front-end.

**DAVE:&nbsp;** You know, if you want your browser to be an API server, for example.

**CHUCK:&nbsp;** Well, it just seem MVC is a nice way of organizing logic and it occurred to me that those who are familiar with the way that the controllers, in particular, here work. If you could get some kind of templating engine on it, and then have an ORM that works well either with APIs or with front-end storage, then you could conceivably make it into a front-end framework, as well. Then, you could have sort of similar systems on the front-end and back-end. But if that kind of extension is not, at least, on the table right now, then it makes it somewhat difficult to get those features in for the front-end to make it viable that way.

**KEITH:&nbsp;** Yeah. That's actually what is really interesting about the GraphQL space, right? And I have like a lot of question marks personally is the point of GraphQL is to make it super easy and straightforward to provide a common language or interface for front-end developers to query a back-end system.

Instead of like a [inaudible] in a pit, and interface sort of being like, "Oh, here's the API endpoint you need to hit, here all the objects that you can possibly interface with, here all of the relationships on one another," just write a query and grab exactly the data you need and then assemble your components on the client based on what you need there. I think GraphQL has the potential to grow into a super, super powerful tool for developers. We're already seeing that in the React community.

So that's where I'm interested in providing a solution. That's not part of Nodal. Nodal would just provide that web server endpoint that accepts the GraphQL query, and Nodal would be your back-end that you can write all your logic for. But that GraphQL is really where it becomes interesting, I think for front-end developers. Then, building tools and STKs in that space on the front-ends would be something separate from Nodal but something very interesting.

**DAVE:&nbsp;** Can you talk a little bit about API payloads? You mention the Nodal, of course, having a template language, and it doesn't use any kind of templating at all so it's up to the developer to generate API response payloads, and to like prescribe what kind of request payloads it will accept, right?

**KEITH:&nbsp;** Yep.

**DAVE:&nbsp;** Are you like limited to JSON? Are there other formats supported? You know, what does it look like?

**KEITH:&nbsp;** We have an API response templates that comes with Nodal that's standardized across the board from most endpoints and it was called the vista respond method where this refers to the current controller so it's the controller respond method. That will automatically format either in array, in object, or a model, or groups of models into that pre-formatted API response that the Nodals used to. That gives you some metadata about the information and saying like, "Okay, here's how many objects are here. If there's an offset in the database created. There's an offset. There's accounts. Amount of total objects if you want to limit the query," that sort of thing. So Nodal takes care of all of that, and will do object nesting, and cool stuff for GraphQL queries.

But there's actually a lot of flexibility there knowing that developers use APIs for different things. Instead of calling the dot respond method, you can call it the dot render method, which accepts objects, which will convert to JSON - just straight JSON, which will accept text, which will just be text. It also accepts just buffers like raw file buffers. If you had the [?] where like maybe, you're using like the image magic library, or something. This one API endpoint has to do multimedia, and return an image, you can still do that with Nodal.

**DAVE:&nbsp;** So you're saying that- I'm not totally sure if I follow, but it sounds like you're saying Nodal does have an opinion about the format and structure of your payloads.

**KEITH:&nbsp;** Yeah. We have a preconfigured format, of view formats for the majority of payloads that you're going to be sending back to the user anyway for Nodal. In terms of accepting payloads, we convert everything into objects when it's received. I mean, we accept objects from- sorry, we accept data from HTTP query parameters. You can send us any post data that you like, so that's not an issue there.

**DAVE:&nbsp;** Is it okay if talk a little bit about the ORM?

**KEITH:&nbsp;** Sure, yeah.

**DAVE:&nbsp;** I'm pretty familiar with the Django ORM, and I've used it exclusively with Postgres. Oh, actually, and little bit SQLite. But you said that your ORM was inspired by Django and Rails. Can you tell us, if there are any interesting things where you are like, "Django or Rails got this wrong, and we're going to do it right in Nodal"? Did you ever have any experiences like that?

**KEITH:&nbsp;** Yeah. ORM in Rails has a lot of flexibility with the ORM in general. But also a lot of methods that kind of simplify common processes was. My experience with Django's ORM is that it's super flexible just by the comparators and like the operators, like for example, having the double underscore GTE (\_\_GTE), saying this field is greater than or equal to whatever.

I think Django really covered the majority of use cases with the simplicity but extensibility of the way that it runs queries. In a way that you can do model relationships by having X double underscore Y double underscore Z (X\_\_Y\_\_Z) for repeated relationships.

That's what I loved about the Django ORM and I wanted to replicate that functionality completely. We didn't have that functionality. It's actually like an interesting story in there. That functionality wasn't a part of Rails and when I first started working with Rails, I got really frustrated that functionality wasn't there, that I couldn't create in that way. So I actually wrote a module with a coworker called FAST API that basically brought the Django ORM or aspects of the Django ORM to Rails.

That project actually got quite a bit of popularity on Hacker News. We haven't maintained it in a while because I kind of took everything we learned from that, and brought it into Nodal. We haven't touched it a lot. It's available at the... Let me check here. I think, it's GitHub.com/TheStorefronts/FASTAPI. You can kind of see what inspired Nodals ORM and then, how we started or how I started thinking about how to build the ORM in Nodal from that. Just because Django was like a class act, and I would to copy it.

**DAVE:&nbsp;** All right, I'm going to go a little bit esoteric on you. So far, you've only talked about ORM for reading data from the database, and Django has one weakness that I know of, and that is outer joins. It just can't do it as far as I understand. Have you had that same problem with the Nodal ORM?

**KEITH:&nbsp;** Yeah. We don't support outer joins right now. With the Nodal ORM, we might in the future. The way that I always tackle problems is go for the most common use case first. I'm very, very interested in having the ORM be as robust as possible because I think it's probably one of the greatest value adds for any framework is really how you can start working with SQL without actually writing SQL. We haven't tackle that problem, yet. But we do supports left join [inaudible].

**DAVE:&nbsp;** So, one more esoteric ORM question. You know what? I’ll save the esoteric one. Let's go to a general one first. How does the Nodal ORM work for updating data in the database - so both inserting and updating?

**KEITH:&nbsp;** This is where we kind of went with Rails-y approach, as well as [inaudible] Django-like approach. This is where the Rails inspiration really came in. You update models and groups of models through what's called this model array interface, which essentially is like a collection of models. You just can do a dot update on models and set all of the fields or to the value to what you want and then just save all of your models at once, with like a dot save all call. That's somewhat similar to the Rails paradigm.

We also have like a standard dot update query where you can actually query for a subset of data, and then call dot update and set everything in that data sets without touching the models at all. Just set everything in that data set to a specific value. We kind of take a couple of approaches there.

**DAVE:&nbsp;** The reason I was going to ask about that is because probably the number one source of ORM bugs for us, on my team, for the last four years is Django's save method on- I mean, individual model instances. The esoteric thing there, and I'm sorry if I'm going too far off at Django-land, but, it saves all fields on the models. If you got model instance and you call save, it will stomp on every single field and then they later added the ability to say, "No, only save these fields," and what you describe works around the problem, it sounds like, because you're forcing users to specify which fields they want to update.

**KEITH:&nbsp;** Well, actually when we do updates, when you do a model dot savecall, we don't save every property of the model. We actually check for what has changed in the mode since it was last retrieved from the database, and then, we specifically save those fields.

**DAVE:&nbsp;** And that's how I think Django should have behaved, but now they're a victim of backward compatibility, and they have to keep doing it that way. I'm pretty sure that's been a conversation in the community. That's really good. Good for you. That's a lesson learned, I think.

**KEITH:&nbsp;** Yeah, for sure.

**DAVE:&nbsp;** So now everyone knows. Nodal is better than Django.

**[Laughter]**

**KEITH:&nbsp;** Well, thank you. I'm not sure that's true. But, thank you.

**AIMEE:&nbsp;** I have one more question. One of the coolest thing about Rails is how easy you could start testing in it. Do you want to talk about that a little bit more in depth?

**KEITH:&nbsp;** Yeah. For actually running test. Cool! I'm really glad you asked this question because this isn't something I'm really happy with in Nodal that I don't have a whole lot of documentation on. When I actually show it to people at meet-ups and people are like, "Wow, I didn't even know [inaudible]." We have a complete test support for actually setting up tests for all of your controllers, specifically focused on controllers to begin with that runs via Mocha. We run the Mocha test suite there. We have a little bit of a wrapper around it just so it's idiomatic and easy to set up.

But you can actually look at the GitHub repository for Nodal. Help me bring it up on talking about it. When you started a Nodal project, it actually automatically creates this runner file which is going to run all of your tests for you, and it's going to create two tests, in example test which is just like a boilerplate, which compares one in one. You expect one should equal one, and does an addition in there. It actually does a test for your index controller to make sure that when you initialize a new project, your index endpoints is actually returning a status of HTTP 200.

That's basically just to show you how tests have start working. Now, we don't have a whole lot of documentation for that, but it's actually, if you just look at how tests are written from those two examples, it's pretty easy to wrap your head around. I'm really happy with that because I mean we come with the Travis. It will creates projects with travis.yml to instantly post to Travis CI, and start running your tests for your Nodal projects. So the support there is full and it's awesome. We just need more docs around it

**DAVE:&nbsp;** Speaking of testing, you may have just mentioned this. The one of the things I really like about Django is that it allows you to exercise your full URL as if you were an API client. Even though, under the hood, it's doing routing. It's not actually going through a server. How does Nodal do that or does it?

**KEITH:&nbsp;** Yeah, I'm looking at the code right now. That's exactly what it does. In tests, they have a method called end point. When you're running a test, you can say this is end point, and then just give it a URL, and it's going to run it through like the same sort of thing. I'm going to spend a whole server to do it, but it's going to run it through the router and then do the calls. You can do this end point, give it a specific URL endpoint, starting with a forward slash and then say 'dot gets' or 'dot post' or 'dot put', etcetera. It's actually do the correct HTTP request.

Then you get the status code back, you get the headers, you get the body. If your response was a JSON response, you also get the JSON response.

**DAVE:&nbsp;** Cool.

**CHUCK:&nbsp;** I have to ask. You said, it was in Version Point 11 right now. When does it get to 1.0?

**[Laughter]**

**KEITH:&nbsp;** That's a good question. The answer is as soon as possible. I would like to have --

**CHUCK:&nbsp;** You're the guy. Just change the version number.

**[Laughter]**

**KEITH:&nbsp;** Tomorrow, it's 1.0. No! I want to make sure before I give a 1.0 that the API is completely stabilized. That means that the future set, that's in Nodal, is not changing from this point forward. We might add to it, but we're not going to remove anything. On the API, the actual interfaces that you're using to interface with the ORM, relationships, or whatever, that doesn't change.

I'm still not 100% happy with the API. I don't think any developer is ever 100% happy with their APIs. You just got to like say, "Okay, it's a 1.0 now," but there are still a couple of large changes that unlikely to make over the next month or two. Once that's done- There are some things that are solidify their wanting, and those are most of things that people have been dealing with already. Like for the most part, the ORM, API is locked in, the model API is locked in, the controller API locked in.

But there's things that we've talked about earlier like related to scheduling and that sort of thing that aren't necessarily locked into the framework. When you push to 1.0, you're making, not just an implicit, an explicit promise to your community, and to the developers using Nodal in production. You're making explicit promises, and say, "We're not going to mess this up on you, and you're going to be supported from here on out." I think, having that trust and that faith is super, super important.

The early adopters, they're okay with changes or whatever. But when you're really heading towards like, "We want enterprise developers to use this," you have to be able to ensure that level of stability. When I put that stamp of approval on there, and say this is 1.0, "This isn't changing. This has been inspected up and down, full tests suite," or whatever. That's the 1.0 mark, and that will be soon but there's still a couple of changes in overall architectural design patterns I want to kind of mess with before I go to 1.0.

**CHUCK:&nbsp;** The other question I have and I had to step out for a minute so I may have missed it, was if somebody wants to start a new project with Nodal, is it just 'npm install -g nodal' and then, 'nodal new' or is there more to it than that?

**KEITH:&nbsp;** That is it, to start with. Right now, if you want to start working with the database, you obviously have to install a Postgres and that's Postgres 9.2. Now, we actually kind of want to get away from that altogether so my view of this space of creating API as in creating systems. In general there's sort of larger vision, is that software developers shouldn't have to think about setting up infrastructure or managing hardware or managing database installs and what not.

But I kind of want to take a different approach to that so I'm pretty sure that over the next couple of months here, we're going to be offering services around this so that you won't have to install Postgres on your own machine, and you're going to be able to use our servers and our services for prototyping. I just want to lower the barrier to entry, as much as possible, so you can get your application up and running as quickly as possible.

**CHUCK:&nbsp;** Is there anything else that we should have asked about Nodal that we didn't?

**KEITH:&nbsp;** I think, you've covered a lot of questions. There is a larger vision outside of the context of Nodal, and the questions that I get asked a lot - one question I asked all the time that we kind of touched on earlier is like, "Do you have like a socket? Do you support web sockets because we want to start building real time systems? And what about Pub-Subbing? All that fun stuff."

My immediate answer is that, well, one as a single human being and developer, there's only so much I can do as a single developer at a time. But I am very, very interested in growing an ecosystem of complimentary software around Nodal, whether that's going with solutions that already exist in the open source community. Somebody has a great single page application framework that plays really well with a back-end and style like Nodal. Whether that's what the ecosystem looks like, or whether we get awesome, brilliant developers coming into the Nodal community saying, "I've got a really good front-end solution here for developers who have a Nodal API back-end." Or, "I have an awesome real time layer that's going to play really well with Nodal when you run it as its own service."

That's where I'm really interested in growing this ecosystem of this space. I think that's older projects and frameworks that being monolithic, have kind of traditionally missed the boat on a little bit is they try to absorb everything. "Oh, this developer want this piece of functionality here. Let's just keep adding it to the framework."

When I think, there's the ability to do a much more communal approach development and saying, "You're going to be building these different types of systems, then API is going to be central, but you're also going to have your SPA. You want real time chat or Pub-Sub or whatever," so use this other service for that and start really bringing up a bunch of services you create in ecosystem with the community. It's something that's really enticing and exciting for me as a space because we can keep projects small and keep working quickly on them.

**CHUCK:&nbsp;** Cool. Well, let's go ahead and get into some Picks. Dave, do you have some Picks for us?

**DAVE:&nbsp;** Oh, you know, I do. So, coming up this September on September 16th this year, 2016. We will be hosting the fifth annual UtahJS Conference here in beautiful Salt Lake City. It's looking to be awesome. We just barely put early-bird tickets on sale and this event is going to be really cool. We have a lot of great people coming in - locals and people from out of state - so I think this is the best kept secret in the JavaScript community, really.

So go over get your tickets at Conf.UtahJS.com and come say hi, if you come to the conference.

**AIMEE:&nbsp;** At UtahJS, who do you have bring in?

**[Laughter]**

**AIMEE:&nbsp;** All of top developers are already there.

**DAVE:&nbsp;** We're already in Utah.

**[Laughter]**

**CHUCK:&nbsp;** Yeah, exactly.

**AIMEE:&nbsp;** Just kidding.

**CHUCK:&nbsp;** Well, we might get one or two from California.

**[Laughter]**

**CHUCK:&nbsp;** All right, Aimee, what are your Picks?

**AIMEE:&nbsp;** Okay, I have two. This one is a really short blog post and it's probably geared towards more like beginner and mid-level developers. It's called 'Writing good code: How to reduce the cognitive overhead of your code'. I think it has very simple tips that you can do. It's based on a book called Code Complete. That's pretty good. It's a short read, and I thought it was worth it.

Then, the second one that I have, it's been a couple of episodes since I pick like a health pick. I started taking it last and again, I only pick stuff because I really do feel like it makes a difference. Someone recommended it to me. It's called the Natural Calm. It's like a magnesium supplement, and so apparently, when your body is under stress for a long period of time, like your magnesium gets depleted.

In the past, you know, because agriculture industry has changed. You can get a lot of magnesium from eating like fruits and vegetables because it was in the soil. But now, that we're doing things a different way, there's not as much in the soil so you don't get magnesium as easily. Anyways, you have to eat like very large amounts in food to get your recommend in daily dose of magnesium. But anyway, this is a drink and I'll put a link in the show notes and I really do feel like it helped. That's it for me.

**CHUCK:&nbsp;** Cool. I've got a couple of Picks. The first one is that, and I've mentioned it to some of the other shows, if you listen to them, sorry. But the first one, I was on vacation last week. We went out to Oklahoma. We're on some private property with a private lake, and it was really nice just to get away.

One of the nicest features of the place we were in was there was no cell service and no internet, which I know some people would go through withdrawals. But for me, it was just nice to not have to worry about any of that. There was no interruption. I can just spend time with my family, and it was a lot of fun. So I'm going to pick that.

One other thing that I'm going to pick. I tried this a few weeks ago. If you're a fan of Saron Yitbarek who will be coming back to Ruby Rogue's Podcast. By the time this comes out, it's going to be public knowledge. She does a Twitter chat every week on Wednesday evening. That's at nine o'clock Eastern, which is seven o'clock Mountain Time for me. It goes for about an hour. She asked a handful of questions on Twitter, and you get to chat with all the other people who are chatting, using the #CodeNewbie.

I really, really enjoyed it. It was a lot of fun. If you want to hop on and have some of those conversations, I'm probably going to be doing it at least for the foreseeable future. I really, really enjoyed it.

There are a couple of things I want to let people know about. This episode will come out right around when Newbie Remote Conf is going on, so if you're a new programmer, and you want to hear some awesome talks aimed at newbies, you can check that out. That's July 13th through 15th. I'm also putting on Robots Remote Conf which is August 10th through 12th. That's Robots and IoT, incidentally.

Then, specifically germane to this podcast - Angular Remote Conf, September 14th through 16th which actually conflicts with UtahJS so you can just do double duty. You can watch it while you're sitting in the UtahJS session. React Remote Conf is going to be October 26th through 28th. Since, we talked about Rails, Rails Remote Conf is going to be October 12th through 14th.

You can find all of those at AllRemoteConfs.com. I'll put a link to that in the show notes, as well as links to each of those conferences. We are still accepting proposal to speak at all of those except for Newbie Remote Conf at this point. So if you are interested at all in speaking then go check out those conferences, and submit a talk.

Also, I'm doing early-bird pricing for those so if you sign up for any of those with a month or more before the conference starts, then you can get the early-bird pricing which at this point is 50% off.

So, anyway, hopefully I stalled long enough for Keith.

**[Laughter]**

**KEITH:&nbsp;** Yeah. My Picks, I would love feedback to the development community in general on one of the medium articles I wrote, talking about modern web development architecture called 'React, IoT, Bots, APIs — Why Web Development Needs a Change', which is kind of my opinion on the future of lab architecture. As well as, I just came across something pretty cool. Somebody builds a Fortran web framework. We're just talking about the frameworks base, and it's kind of --

**DAVE:&nbsp;** Fortran communities always write a new framework.

**[Laughter]**

**DAVE:&nbsp;** I have kind of Fortran fatigue.

**[Laughter]**

**KEITH:&nbsp;** It's kind of cute. It's a cool project. It's a very impressive project. It's on GitHub Mapmeld/Fortran-machine. People should check it out. A good amount of effort went into it.

**CHUCK:&nbsp;** All right, well, if people want to find out more about Nodal or check in what you're doing, what should I do?

**KEITH:&nbsp;** Nodal is available on GitHub, which is just on my GitHub Keithwhor/Nodal. Feel free to- I mean, contributions are completely open. You have to submit a PR but we're always looking for community contributors and people to really help push the needle forward. When I talk about building systems, I had actually founded a startup called Polybit. We were focused on providing infrastructure solutions for developers who are building systems like API services with Nodal.

When I talk about those other types of systems, like real time systems, launching SPAs, and things like that, building infrastructural solutions specifically focused around those system types. You can check that out at Polybit.com, and keep in touch. We're actively hiring. If you're talented JavaScript developer and you want to join something cool, feel free to email me directly.

**DAVE:&nbsp;** I got to go back to that Fortran thing. On their website, this is an MVC web stack, written in Fortran 90 so you get a raise, and it's not punch cards.

**[Laughter]**

**CHUCK:&nbsp;** There's a glowing recommendation right there, "It's not punch cards".

**DAVE:&nbsp;** I know! I'm so tired of writing my web framer in punch cards.

**CHUCK:&nbsp;** I know, right?

**DAVE:&nbsp;** This is so cool.

**CHUCK:&nbsp;** All right, we'll go ahead and wrap up the show. We'll catch you all next week.

**_[Bandwidth for this segment is provided by CacheFly, the world’s fastest CDN. Deliver your content fast with CacheFly. Visit CacheFly.com to learn more.]_**

**_[Do you wish you could be part of the discussion on JavaScript Jabber? Do you have a burning question for one of our guests? Now you can join the action at our membership forum. You can sign up at JavaScriptJabber.com/Jabber and there you can join discussions with the regular panelists and our guests.]_**
