# Week 0024 "Deploy with Git Hooks"
**2015-11-09**

If you are already using Git to manage your source, it's not much of a leap to
use it for triggering the deployment of your project to your staging or production
servers.

## Topics

* What are Git hooks and how do they work
* Setting up hooks to trigger on various actions
* Creating simple bash scripts to take actions when a hook triggers

#### Not using Git?
Shame on you.  No, seriously, at least take the time to get a basic repo started
that you can use to back out changes when you break something. It's super easy.

#### Got a project you want to do this for?
Bring your own project to the talk tonight and we'll see if we can get you setup
with automated deployments using Git Hooks.

### Talk Resources
Want to learn some before coming out?

* [Git on the Server] (https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server)
* [How To Set Up a Private Git Server on a VPS](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-git-server-on-a-vps)
* [Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
* [Bash Scripting](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

### Platform-specific examples:
* [Azure Github Deploy Hooks](https://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/) Used on the [Leagify Draft Charts site](http://draftcharts.azurewebsites.net/) from [this github repo](https://github.com/Leagueify/draftcharts-jetstrap)
* [Heroku Deploy Hooks](https://devcenter.heroku.com/articles/github-integration)
* [Google App Engine deployment triggers](https://cloud.google.com/tools/cloud-repositories/docs/push-to-deploy#connect_your_git_repository_to_the_cloud_source_repository)
* [Resin.io using git hooks to push to devices](https://resin.io/how-it-works/)
* [Using AWS CodeDeploy to deploy from GitHub](http://docs.aws.amazon.com/codedeploy/latest/userguide/github-integ.html)
