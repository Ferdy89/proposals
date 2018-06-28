# Using Docker in Development, Test and Production

## Abstract

Reading HackerNews one might get the impression that using Docker is the
solution to all of your problems. Then you try to actually deploy a container
to production and you realize it’s not so trivial. Running your build with
containers in your CI environment turns out to be problematic and using Docker
for your local development is very inefficient.

If you want to jump onto the Docker train but don’t know where to start, this
talk will show you many ways you can get started. You will learn when
containers are a good idea and when they might be problematic for your team.

## Details

Docker has gained a lot of popularity in the past years because it simplifies
many problems related to portability. It basically is a way of creating very
lightweight Linux virtual environments in a simple and reproducible way. There
is also a huge community that is creating a lot of different containers and
publishing them online.

This makes it very simple to, for example, set up a local environment with
Rails, Postgres and Redis. It also makes it simple to run your tests against
multiple Ruby versions automatically, or to make a project trivial to install
locally. It’s also very respectful with your machine’s resources: you can spin
containers up and down with very little cost! And it stays fast because it is a
thin layer on top your machine’s kernel.

Having heard all of that, it’s hard not to feel like you’re missing out if
you’re not using Docker for everything. However, there are many caveats that
you might want to consider before you put all your code inside of a container.
This talk will explore the pros and cons of using Docker in different typical
situations for a Ruby developer.

### Production

If you are using Ruby to develop a web application, deploying it as a container
is one of the most popular use cases for Docker. The reason is that using a
virtualization layer makes it very predictable to know how will it behave
regardless of where is the code really running, and who likes surprises in
production? Because it is such a popular use case, it’s probably the one there
are more documentation and support for.

In order to illustrate the advantages of using containers in production, I will
compare the experience of deploying an application with tools like Capistrano
to a deployment with Heroku, which uses a virtualization layer similar to
Docker containers. After that, I will compare the experience of deploying with
Heroku to deploying Docker containers on a popular service like Amazon’s
Elastic Container Service. By comparing all three alternatives one by the
other, I’ll enumerate the pros and cons of using containers as opposed to
traditional git-pull deployments.

### Test

The next environment I’ll be analyzing is the test one. Tests are interesting
because we run them both on our development machines and often also on CI
servers in the cloud. We also tend to have special dependencies like browsers
for our system tests which might be difficult to run inside of a container
without an X windows system.

The experience of running tests inside a container on a development machine
resembles a lot the experience of running development code. Because of this,
this section will mostly focus on how to get our tests to run inside of a
container in a CI environment. I will be running through a common way of
setting up CI to run tests with Docker, which includes building the container
from an image and running tests on it. I will also briefly go through a list of
things that containers make very simple, like running builds in parallel or
running tests against different machines (very useful for gem maintainers who
need to ensure portability).

After having explained what the happy path for running Docker in CI looks like,
I will dive into some of the issues that you might run into. Some of these
issues might be:

* Your CI runners might already be running in containers, and there’s special
  configuration that’s needed to run Docker in Docker.
* Building the container from scratch (having to install all packages and gems)
  can take a long time. Ideally, you will want to cache part of that building
  process to speed up your test builds, but that requires a Docker Registry.
* Docker images don’t have an X windows system by default, so running system
  tests requires extra installation.
* You might need a different Dockerfile if your production one doesn’t install
  gems in the test group, but you also don’t want to have two copies of very
  similar Dockerfiles.

Finally, I’ll be raising the question of whether or not is it worth it to set
up Docker in CI. On the one hand, it takes extra work to set it up; on the
other hand, it closes the gap from running tests locally vs CI.

### Development

The last part of the talk will be dedicated to running your code inside of a
Docker container locally. This is the most difficult part because we want to be
in full control of our development environment but having Docker in between us
and our code can limit some of our tools. On the other hand, it can reduce the
setup of complicated dependencies to one command, even if your project depends
on PostgreSQL, Redis or any other processes.

There are many different aspects to be considered when attempting to use Docker
in development. The reasons for using it or avoiding it will massively depend
on the circumstances around your team and your infrastructure. These are some
of the points that I will be analyzing so you can make informed decisions about
whether this is good for your codebase:

* How to achieve automatic code reload when running a local Rails server.
* How to avoid having to rebuild your Docker image constantly after any change
  to the code.
* What is the performance of sharing filesystems with a Docker container when
  running on a Mac? Not running a native Linux kernel has huge implications.
* How to have gems installed locally to be able to use ctags to traverse code
  from your local text editor.
* Using Docker avoids the need to use tools like RVM or having to deal with
  having multiple PostgreSQL versions installed.
* How to use tools like Docker Compose to have your whole infrastructure
  codified on a simple YAML file that can be in source control.

## Pitch

Docker seems to be gaining a lot of popularity in the recent years because of
how great it is at hiding the complexity of the infrastructure underneath the
code. It just so happens that that is one of Ruby’s greatest beauties as well!
Together, they make a combination that’s hard to beat in terms of simplicity
for the user.

In the last few years, I’ve tried to invest in Docker to make sure my
applications were staying ahead of the curve. At my job I build tools for other
developers, so ease to use and portability are of great importance to me.

This hasn’t been always the most pleasant experience because Docker is a very
new technology and it’s still being discovered in many ways. With this talk, I
intend to share my experiences. Hopefully, other people don’t need to relive
the same painful situations and can become productive much faster than did.
