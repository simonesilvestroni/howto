# Blame the implementation, not the technique

[TimKadlec.com](https://timkadlec.com/ "Visit Tim Kadlec’s website")

`04/04/2013 21:29`

Stop me if you’ve heard this one before.

> “Responsive design is bad for performance.”
> “User agent detection is bad. Don’t segment the web.”
> “Hybrid apps don’t work as well as native apps.”
> “CSS preprocessors shouldn’t be used because they create bloated CSS.”

If you create for the web you’ve no doubt heard at least a couple of these statements. They’re flung around with alarming frequency.

There is a fundamental problem with this line of thinking: it places the blame on the technique instead of the way the technique was implemented. Generalizing in this way discredits the validity of an approach based on poor execution, and that’s a very harmful way of thinking.

With any of the examples above, the technology itself wasn’t the problem. CSS pre-processors, PhoneGap, user agent detection, responsive design — these are tools. They are neither inherently bad or good. Their quality depends on the way you wield them.

I’m not a carpenter. If you asked me to build a table you would end up with a lop- sided, three-legged abomination. That’s not because of the hammer, or the saw, or the drill—that’s because I suck at using them. Give the same equipment to a carpenter and you get something beautiful.

It’s no different with our own tools.

When someone builds a 4MB responsive site, blame the implementation. There is no reason why a responsive design can’t perform well. If you take the time to carefully build from a base experience up, only loading assets as needed and using patterns like the anchor include pattern to keep things light along the way, a responsive site can look beautiful and load quickly.

When someone builds a site and uses server-side detection to exclude some browsers or devices from the experience, blame the implementation. There’s nothing evil about user agent detection. You don’t have to use it to segment experiences. In fact, it’s quite handy as a compliment to feature detection. Consider that some devices can make phone calls, and that those devices don’t all agree on the same protocol. Start with a smart default. Use server-side detection to try to determine which protocol should be used. If a value is reported use that. You’re enhancing the experience where you can and offering something usable where you can’t. There’s nothing wrong with that.

The same goes for using hybrid applications, CSS preprocessors, text editors or any number of tools. They’re only as good as the person using them. If you get to know them, identify their strengths and weaknesses and use them when appropriate, they can be really powerful and helpful additions to your toolbox.

It’s all too easy to cling to the one or two tools we’re most comfortable with and dis- count the rest. Luca Passani hammered (no pun intended) this home in a recent post. He was discussing the oft-mentioned responsive web design (RWD) vs server-side detection debate and came to a very sound conclusion:

> In this context, isn’t the discussion between RWD and {device-detection} a direct corollary of the old “when all you have is a hammer, every problem looks like a nail”? and of course, doesn’t this apply also the other way around, with backend developers favoring a solution to device fragmentation that leverages the tools they know best?

Experiment with techniques before you condemn them. Find out for yourself if the tool is really where the blame should be placed.
Building great experiences on the web isn’t getting any easier. We need all the tools we can get. Don’t discredit them simply because someone uses them poorly.

---

URL: [http://timkadlec.com/2012/10/blame-the-implementation-not-the-technique/](http://timkadlec.com/2012/10/blame-the-implementation-not-the-technique/ "See the orginal article on Tim Kadlec’s website")

---

#WebDesign