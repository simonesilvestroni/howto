# Performance As Design

## Brad Frost

`04/04/2013 21:29`

Too often, any talk of web performance quickly ventures into the land of heavy geekery. Terms like DNS lookups, Gzipping, minifying, far future expires headers, caching, ETags and more are thrown around and consequently lose the attention of most non-techy people. This perpetuates a mentality that performance is solely a technical concern that only developers need to concern themselves with.

It’s time for us to treat performance as an essential design feature, not just as a technical best practice.

## We all feel it

From time to time I get asked what I do for a living. Whenever I mention that I work in mobile, I’ve had people immediately react "FACEBOOK SUCKS!"

Why such an immediate, visceral reaction? They aren’t reacting to the intuitiveness of Facebook’s navigation, nor questioning the elegance of the Timeline redesign. The whole [Facebook clusterfudge](http://techcrunch.com/2012/09/11/mark-zuckerberg-our-biggest-mistake-with-mobile-was-betting-too-much-on-html5/) had everything to do with the fact that their app was *slow as shit*.

![performance-as-design-02](Performance As Design.assets/performance-as-design-02.jpg)

The average web page is [increasingly obese](http://www.webperformancetoday.com/2012/05/24/average-web-page-size-1-mb/). We now have more toys to play with, and that means more potential to do damage. [Phil Hawksworth](http://hawksworx.com/) brilliantly called out the ridiculousness of these [gratuitous, parallaxified websites](http://www.milwaukeepolicenews.com/):

![performance-as-design-01](Performance As Design.assets/performance-as-design-01.jpg)

> If your website is 15MB it’s not HTML5, it’s stupid.

[Christian Heilmann](https://hacks.mozilla.org/2012/10/broken-promises-of-html5-and-whats-next-a-presentation-at-html5devconf/)

While these sites may be visually arresting (though for a lot of them that’s certainly debatable), a good many visitors will never stick around to see them. [74% of mobile web users](http://www.digitalmall.us/1150/smartphone-users-frustrated-with-mobile-web-experience/) will leave a site if it takes longer than 5 seconds to load. That means you have 5 seconds of someone’s time to get them what they want, or they’re gone.

## Good performance is good design

The road towards better performance doesn’t start with developers or technology stacks (though I’m certainly not suggesting those things are unimportant). It begins with a shared interest on everyone’s part in making a product that’s lightning fast. Some things to consider:

- **Include performance in project documents**—Statements of work, project proposals and design briefs should explicitly and repeatedly call out performance as a primary goal. “The goal of this project is to create a stunning, flexible, lightning- fast experience...”

- **Get designs into the browser as soon as possible**—A picture of a website design comp hanging on a wall may look purdy, but it’s a terribly unrealistic way of gauging how effective the design will be once it exists in its final environ- ment. As we enter The [Post-PSD Era](http://bradfrostweb.com/blog/post/the-post-psd-era/), we’re able to see performance implications of a design direction much sooner than a traditional waterfall process.

- **Test on real devices**—[Stephanie Rieger](http://stephanierieger.com/on-designing-content-out-a-response-to-zeldman-and-others/) properly states that it’s impossible to gauge a design’s performance in a shrunken viewport or emulator. It’s essential to test and test early on real devices to see the true ramifications of every inter- face element you introduce into your designs.

- **Collaborate**—Developers should be involved early on in the design process and should call out potential performance concerns in wireframes and comps. It’s important that this process isn’t just a yes/no grunting match, rather a truly col- laborative session between disciplines.

- **Educate**—Many people in the design process simply don’t know a lot of perfor- mance consequences of their design decisions. Help them understand that in- cluding five font faces is going to do some damage. Help them think twice about adding tons of massive images. Do a quick prototype in [Codepen](http://codepen.io/) to demon- strate an idea, then sit together and use it on a real device on a 3G connection.

Ultimately performance is about respect. Respect your users’ time and they will be more likely to walk away with a positive experience. Good performance is good de- sign. It’s time we treat it as such.

> **`SOURCE`**
> 
> [http://bradfrostweb.com/blog/post/performance-as-design/](http://bradfrostweb.com/blog/post/performance-as-design/ "See the original article on Brad Frost’s website")

---

#WebDesign