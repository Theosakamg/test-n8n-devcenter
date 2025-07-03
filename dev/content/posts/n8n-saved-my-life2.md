---
title: "How n8n saved our Advocacy impact on Social Media!"
subtitle: ""
date: 2025-07-03T15:04:20+01:00
image: /images/n8n-saved-my-life/social-media.jpeg
image_alt: "Social Media apps on a phone"

icon: tutorial
featured: true
author:
  - flovntp

sidebar:
  exclude: true

type: post

description: |
  Learn how n8n workflows improve internal communication and amplify our Advocacy social media impact.
  
tags:
  - n8n
  - nocode
  - social networking
  - tutorial
categories:
  - featured
  - use-cases
math: false
# excludeSearch: true
---
In a [previous article](/posts/nocode-n8n/), we explained how to host [**n8n**](https://n8n.io/) on [**Upsun**](https://www.upsun.com).  
Since then, we've been using n8n to automate our internal workflows — and one pain point in particular has been solved: promoting our DevCenter technical blogposts!

In the Advocacy team, our mission is to publish high-quality, relevant technical blogposts across a variety of topics — ideally with strong engagement.  
But until recently, promotion on social media was a **manual process**, handled by our wonderful and brilliant teammate Celeste. 🧠💪

And as with any manual process, miscommunication sometimes occurred:
- Sometimes the Advocacy team forgot to ping Celeste with a summary and link.
- Sometimes Celeste was too busy and missed the momentum for promotion.

### This is now history! 🚀

We've built an **n8n workflow** that **automatically sends a Slack message** to our marketing team whenever a new blogpost is published.  
It extracts key metadata (title, URL, image), uses **OpenAI to generate a tweet**, and notifies our `#marketing` Slack channel — complete with a pre-written tweet.

> 💡 If you're reading this article *because of a tweet* — then it worked!

## Our old workflow (RIP)

Before this automation, our flow looked like this:
1. Write the article on a new Git branch.
2. Open a Pull Request on the [DevCenter GitHub repo](https://github.com/upsun/devcenter).
3. ask teammates to review the online version of the blogpost (or the series) via the [Upsun preview environment](https://docs.upsun.com/glossary.html#preview-environment), which is automatically linked in the Pull Request as a comment.
4. Once merged, manually ping the marketing team with the article and a short summary.
5. The marketing team would write a tweet and schedule it for social media.

## Our new workflow 🎉

Here’s how it works now:
1. Write the article and open a PR, as usual.
2. Once merged, **n8n detects the new blogpost(s)**.
3. n8n extracts the title(s), author(s), and image(s).
4. It uses **OpenAI to generate a tweet**.
5. It **automatically pings the `#marketing` Slack channel** with everything the team needs.

## Why this automation matters

- **⏱️ Time saved for both teams**  
  Marketing no longer needs to read every blogpost — they receive a tweet-ready summary instantly.

- **⚡ Increased reactivity**  
  Blogposts are promoted as soon as they're live, improving reach and engagement.

- **🤝 Better collaboration**  
  Automation ensures that nothing falls through the cracks, and that both teams stay aligned.

- **📢 Consistent messaging**  
  OpenAI-generated summaries keep tone and clarity consistent across posts.

- **📈 Scalable promotion**  
  As our content production scales, we keep a strong social presence without increasing manual effort.

## Behind the scenes: How it works

{{< figure src="/images/n8n-saved-my-life/n8n-workflow.png" alt="n8n workflow Slack message" >}}

1. **GitHub Webhook Trigger**  
   The workflow listens for push events on the DevCenter repo.

2. **Metadata Extraction**  
   It extracts new `.md` files, ignores edits to old posts, and parses frontmatter (title, authors, image).

3. **Tweet Generation**  
   OpenAI creates a short, clear tweet summarizing the article.

4. **Slack Notification**  
   It posts to `#marketing` with:
    - Article title
    - GitHub authors (linked)
    - Article URL
    - Tweet suggestion
    - Thumbnail image


## Final Result: What It Looks Like

Here’s an example of the Slack message sent by the workflow:

{{< figure src="/images/n8n-saved-my-life/workflow-result.png" alt="n8n workflow Slack message" >}}

## Want to build it yourself?

You can grab the exported n8n workflow [here](#TODO).  
Once imported into your n8n instance, configure the following:

- 🔑 **Credentials**: Add OpenAI, GitHub, and Slack credentials from your [n8n account](https://docs.n8n.io/credentials/).
- 🔗 **GitHub Repo**: Update the repo URL in the `Github Repo DevCenter` trigger block.
- 👤 **Author Extraction Logic**: On our DevCenter, authors are listed with GitHub usernames. Update this logic if yours differs in the `Extract Title+authors+image` block.

## Conclusion

This automation boosted our Advocacy impact by bridging content creation and promotion — instantly and with minimal effort.  
It keeps both the Advocacy and Marketing teams in sync, and speeds up social sharing of our technical content.

If you're managing internal content workflows and want to scale your reach without scaling your workload:  
**Try n8n. Add OpenAI. Automate the boring parts.**

Happy automating! 🚀
