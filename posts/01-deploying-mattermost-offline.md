# Why we chose Mattermost and how to deploy it in an offline-environment
*First published **2021-01-15***

## What is Mattermost?

To quote the company themselves
>[Mattermost](https://mattermost.com/) is an open-source, self-hosted alternative to [Slack](https://slack.com).

Most developers, system administrators, DevOps engineers and others have encountered Slack at some point in their career, and why shouldn't they have? Slack is great! 

So why would we consider an alternative to Slack, such as Mattermost?

### Security regulations

For us the biggest advantage Mattermost had over Slack was simply the fact that we could host it in our on-premise infrastructure.

If you're working in a company that's handling sensitive data, leveraging the cloud or Software as a Service (SaaS), might not be an option.


### Pricing

The (self-hosted) [enterprise licenses](https://mattermost.com/pricing-self-managed/) is cheaper per user than for [Slack](https://slack.com/intl/en-no/pricing). Which might be worth taking into consideration when deciding on a chat solution.

## What do we use Mattermost for?

So what do *we* actually use Mattermost for?

### Chat service

Our initial need when looking for a chat solution was for something to replace our on-site Pidgin-chat.

We needed to be able to chat within the different teams in our organization, for one-on-one chats and of course for off-topic jibber-jabber.

I especially love how we are able to paste different code with correct syntax highlighting in Mattermost. Being able to quickly show and get feedback on small(ish) snippets of code is *very* neat to have when working in an R&D environment!

### Build status reporting

Like Slack, Mattermost does have good support for allowing incoming webhooks to post messages to certain channels.

We have set up a webhook for our CI/CD toolchain to tell us the build status for pull requests, tagging the author of the builds.

### AWX failure reports

Whenever our [AWX](https://www.ansible.com/products/awx-project)-instance is failing on hosts, I want to be notified. This is done using an incoming webhook.

### Sending files

While sending files is not our main purpose of having an on-premise Mattermost, it is neat to be able to do it from time to time.


## Deploying Mattermost on Docker in an offline environment

The Mattermost homepage has an extensive documentation on how to [install the server](https://docs.mattermost.com/guides/administrator.html#installing-mattermost) in different environments.

What I'm going to focus on here is how to deploy Mattermost using Docker-compose and [this community guide](https://docs.mattermost.com/install/prod-docker.html)