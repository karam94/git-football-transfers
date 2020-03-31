# git-football-transfers

## 11 - Trunk based development

### Well done

If you've reached this point, then well done. You should now have enough core knowledge around Git to get you by on a day to day basis.

Remember that a lot of what you learned can be replaced with a GUI tool - discussed in the next module.

However, whether you have a GUI or not, it is important that concepts around merging, rebasing & so forth make sense to you because a GUI cannot think for you. The underlying understanding is important. The same way an IDE cannot write or outright refactor code for you. It can help you, but you still do the majority of the driving through your underlying knowledge.

Within this section, you won't learn anything new specifically to do with the technical aspects of Git past this point. This is just a chapter where I go on a bit of a rant.

I do however think that it's worth a read, since you're probably a budding software developer (who also lacks hands-on experience with source control in the real world - hence why you're here - which isn't a bad thing) and I think it's important that you are aware of the fact that even though you've probably just spent the last couple of hours learning about branching strategies and dealing with huge merge conflicts, that there's no unwritten software development rule that says this is how it always needs to be!

It might seem ironic after everything we've discussed so far throughout this crash course, to read that I actually dislike branching strategies and employing them within most software development teams.

In fact, some people feel so strongly about this that there are even books on it... and empirical evidence to prove it! So I won't say that it is a controversial opinion, either.

If you're reading on, trunk based development is when features are developed and basically, pushed straight to the master branch. Sounds crazy, right?

### Don't add complexity, for the sake of adding complexity

So, cutting to the chase. Why do I dislike branching strategies?

Well. I'm a firm believer in always using the right tools, for the right job.

Sometimes you have extremely large and dysfunctional development teams, mainframe systems, a significant lack of dev ops culture, where a branching strategy becomes an undoubted necessity and requirement.

But sometimes in some places, the biggest hurdle stopping development teams moving to this approach is often down to culture and often that culture stems from outside of the development team itself, which I'd rather not focus on otherwise we'd be here all day.

From a more technical perspective, most of the time you have relatively small (3-8 developers on average), closely knit, development teams maintaining numerous small sized repositories, writing relatively modern software, using some sort of Gitflow-like approach with small relatively short-lived feature branches, with some sort of continuous integration pipeline available (there's no excuse not to have one nowadays anyways).

Basically, a team that could easily employ trunk based development if they were either A) allowed to do so by management or B) willing to give it a try and not just sticking with what they've been doing for the last 10 years.

Just to leave you with some food for thought...

Short-lived feature branches, means short spans of development to deliver a feature or user story. This means it isn't likely that too many people at once, due to the nature of smaller, collaborative teams, will step on each others toes and even if they do, since both are pushes directly to master then they are likely to have to solve a merge conflict (that is probably quite small at this point) earlier than previously where it would only come to fruition upon merging both branches on the back of a pull request (PR). If someone pushes code to master that breaks the build, this is also evidently significantly quicker feedback to the development team. Quicker feedback loops are a good thing, don't you think?

Another example where the quicker feedback loop is useful can be where one person (or pair) is implementing a feature in the same repository of a colleague. Even if a merge conflict doesn't occur, they should be regularly pulling down updates from master. Spot improvements for each other quicker in the development process... don't wait for the awful PR stage where most people hate being put under the spotlight & critiqued anyways.

WAIT THOUGH, but if something goes wrong, the master branch is always there as a branch we know contains a working version of the software that can always be deployed or rolled back to. Right?
WAIT THOUGH, but if I'm pushing straight to master and my work isn't finished... how are any deployments supposed to happen? We can't be deploying my unfinished code can we?

Correct, but most continuous integration/deployment options store the artefacts of previous deployments. One of their selling points is one click roll backs to avoid us having to worry about it and maintaining a god-like "master" branch.

As for deploying unfinished code... use feature switches! Most of the time you won't be re-inventing the wheel, swapping SQL out for MongoDB and leaving the repository in a mess on master whilst a colleague is also coincidentally implementing some other feature. You'll be adding a new endpoint to something or making a couple of tweaks here and there.

If you cannot/don't have the confidence to merge in to trunk/master daily, ask yourself why. A common pitfall is usually, tasks just being too large or just not accommodating/caring enough about the way development occurs to develop with a mindset that simultaneously prioritises keeping the software functional on master for the greater good of the team.

Going back to the SQL to MongoDB migration example... if you know a release has to go out and that your migration will take a while, develop separate repositories (within the software type repositories that do the data persistance, not Git repos) that obviously have tests around them (right?), but your dependency injection container will still resolve to the SQL ones until you are ready to switch both out. This way your unfinished code can be safely deployed as you have a natural feature switch. Why? Because you collaborated with the rest of your team. You didn't hide yourself behind a feature branch with headphones on in the corner and then complain about massive merge conflicts when you re-emerge out of the dark after a weeks worth of development.

I'll stop now, but hopefully I've planted some food for thought to reflect against branching strategies with.

One thing I always tell people is that proper continuous integration & trunk based development is an addiction. Once you experience it, there's no going back. I cannot count on my fingers how many times I've deployed things whilst stuck in traffic in my car or whilst having a coffee in Starbucks... or even better... trusted a colleague to actually deploy their code without needing any sort of silly PR acceptance from me, a member of the management (who probably hasn't written a line of code in 10 years) or anyone else for that matter :)

Like I said... food for thought... and anything that means I don't have to sit in a retrospective listening to people argue over MASSIVE merge conflicts that became apparent after a weeks worth of development for an hour ever again in my life.
