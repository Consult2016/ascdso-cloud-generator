# word-cloud-generator
It's a golang web app that takes a block of text and turns it into a word cloud.

## Notice
This project is under active development. This project is being created as a sample app for an upcoming training class on Continuous Delivery with Lynda.com. You can see previous courses we have made at https://lynda.com/JamesWickett. Thanks!

## Prerequisites
1. Install go - https://golang.org/doc/install (Start learning go with the tour - http://tour.golang.org/)
2. Set $GOPATH `export GOPATH="${HOME}/go"`
3. Set $PATH `export PATH=$PATH:$(go env GOPATH)/bin`
4. Install godep - `go get github.com/tools/godep`
5. Install goconvey - `go get github.com/smartystreets/goconvey`
5. Install rice - `go get github.com/GeertJohan/go.rice/rice`

## Git
We use git hooks to standardize development on the project. Please run `make git-hooks` to get started.

## Using Make

### Building Artifacts
This will pull down dependencies, run unit tests, and compile a linux, mac and windows binary into ./artifacts.

`make`

### Fiddling Around

You can build and install a copy in your local $GOPATH/bin directory with:

```
make install
```

### Clean up previous build files
```
make clean
```

### Test Coverage
```
make test
```

### Visual Test Coverage
```
make goconvey
```

### Bundle HTML and JS
```
make rice
```

### To Run
`make run` or just run the executable.  It will run as a daemon and bind to port 8888, and you can see it by going to http://localhost:8888 in your browser.

## Use API via Curl
```
$ curl -H "Content-Type: application/json" -d '{"text":"ths is a really really really important thing this is"}' http://localhost:8888/api
```

## Setup example
Use this setup

aws_access_key_id = AKIAIOSFODNN7EXAMPLE
aws_secret_access_key = wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

## DevOps Foundations Handout

DevOps Foundations: Continuous Deliverywith James Wickett and Ernest Mueller1DevOps Foundations: Continuous DeliverywithJames Wickettand Ernest Mueller____________________________________________________________________________________Would you like to know more?This handout provides definitions of terms used in the course as well as links to the topics, tools, and resources we reference. IndexIntroductionChapter 1: Continuous Integration and Continuous DeliveryMust-ReadDefinitionsBenefitsBuild PipelinesChapter 2: Build Your Own PipelineVersion ControlSCM ToolsContinuous IntegrationContinuous Integration PracticesNotesCI Server ToolsBuild ToolsArtifact RepositoryArtifact Repo ToolsTestingTesting ToolsDeploymentDeploy ToolsChapter 3: Putting It All TogetherThe Continuous Delivery PipelineIntroductionYour fearless instructors are James Wickett (@wickett) and Ernest Mueller (@ernestmueller).The Agile Admin bloghttps://theagileadmin.com/
DevOps Foundations: Continuous Deliverywith James Wickett and Ernest Mueller2Signal Scienceshttps://www.signalsciences.comhttps://labs.signalsciences.comAlienVaulthttps://alienvault.comhttps://otx.alienvault.com/Chapter 1: Continuous Integration and Continuous DeliverySmall + Fast = BetterMust-Read CI/CD ResourcesContinuous Delivery, by Jez Humble and David Farley https://www.amazon.com/Continuous-Delivery-Deployment-Automation-Addison-Wesley/dp/0321601912And in website formhttps://continuousdelivery.com/DefinitionsContinuous integrationis the practice of automatically building and unit testing an entire application frequently, ideally on every source code check-in—dozens of times a day if necessary.Continuous deliveryis the additional practiceof deploying every change to a production-like environment and performing automated integration and acceptance testing after it passes its build and unit tests.Continuous deploymentextends this concept to where every change goes through full automated testing and is deployed automatically to the production environment.  BenefitsContinuous delivery has the following benefits.●Empowering teams●Lowered cycle time (shortens lead times for changes, time to market goes down,lower MTTR)●Better security (and quality increases,not decreases)
DevOps Foundations: Continuous Deliverywith James Wickett and Ernest Mueller3●Rhythm of practice (limits your work in progress)●More time to be productiveBuild PipelinesCD pipelines consist of the following components.●Source code repository●Build server●Unit tests●Artifact repository●Deployer●Integration tests●End-to-end tests●Security (and other specialized) testsTypes of testing●Unit testing●Code hygiene●Integration testing●TDD/BDD/ATDD●Infrastructure testing●Performance testing●Security testingThe difference between TDD, BDD, and ATDDhttp://www.assertselenium.com/atdd/difference-between-tdd-bdd-atdd/
DevOps Foundations: Continuous Deliverywith James Wickett and Ernest Mueller4Chapter 2: Build Your Own PipelineThe sample word cloud generator apphttps://github.com/wickett/word-cloud-generatorVersion ControlGet started on GitHubhttps://github.com/Setup SSH keyhttps://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/SCM ToolsGithttps://git-scm.com/On a Mac, `brew install git`But also...Subversionhttps://subversion.apache.org/GitHubhttps://github.com/Bitbuckethttps://bitbucket.org/Perforcehttps://www.perforce.com/Continuous IntegrationContinuous Integration PracticesA CI culture•Start with a clean environment•Builds should pass the coffee test (<5 minutes)
DevOps Foundations: Continuous Deliverywith James Wickett and Ernest Mueller5•Run tests locally before committing•Don’t commit new code on broken builds•Don’t leave the build broken•Don’t remove failing testsNotesInstalling go for yourselfhttps://golang.org/doc/installCompiling go in Jenkinshttps://golang.org/cmd/go/#hdr-Compile_and_run_Go_programhttp://www.snowfrog.net/2013/06/18/golang-building-with-makefile-and-jenkins/Godep for dependencieshttps://www.goinggo.net/2013/10/manage-dependencies-with-godep.htmlInjecting secrets into Jenkins build jobshttps://support.cloudbees.com/hc/en-us/articles/203802500-Injecting-Secrets-into-Jenkins-Build-JobsInteresting .gitignore so we can keep the jenkins_home in Githttps://github.com/github/gitignore/pull/1763/commits/5263ddbf7e4173462838a3461ba827e2bd2b5635Some of our build script is making sure the GOROOT and GOPATH are the weird way go expects them.https://stackoverflow.com/questions/37262712/jenkin-build-setup-for-go-projectsCI Server ToolsJenkinshttps://jenkins.io/https://hub.docker.com/_/jenkins/https://plugins.jenkins.io/https://jenkins.io/doc/book/pipeline/But also...GoCDhttps://www.go.cd/Bamboohttps://www.atlassian.com/software/bamboo
DevOps Foundations: Continuous Deliverywith James Wickett and Ernest Mueller6TeamCityhttps://www.jetbrains.com/teamcity/Travis CIhttps://travis-ci.org/CircleCIhttps://circleci.com/Build ToolsMakehttps://www.gnu.org/software/make/Rakehttps://github.com/ruby/rakeMavenhttps://maven.apache.org/Gulphttp://gulpjs.com/Packerhttps://www.packer.io/fpmhttps://github.com/jordansissel/fpm/wikiArtifact RepositoryUse artifacts for●Reliability●Composability●Security●ShareabilityPlan ahead1.Packaging format(s)2.Dependency management3.Artifact repoNexus docs
