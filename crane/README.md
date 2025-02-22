# Crane Hackathon

## Event #1 (December)

### Agenda - day 1 (Monday, Dec 13th)
* 9:00am Getting ready for today and tomorrow
* 9:10am Quick update on Crane
* 9:45-11:45am  Getting started together
* 1pm-5pm Running through scenarios, answering questions, filing BZs, etc...

### Agenda - day 2 (Tuesday, Dec 14th)
* 9:00am Monday recap
* 9:15am Discussion with Engineering, early feedback, etc.
* 10am More hands-on on scenarios
* 3pm Retro on what we learnt + Capture final feedback, questions, improvements, etc. 


## Links

* [Agenda and Intro slides](https://docs.google.com/presentation/d/1pOZOTv_8p9lIKbp8-R5291OfyMGkdZDTT9AYxSVgJTU/edit?usp=sharing)
* [Upstream Documentation](https://crane-docs.konveyor.io)
* [Documentation Github](https://github.com/konveyor/crane-documentation): File issues with docs here
* [Crane Github](https://github.com/konveyor/crane): File bugs or RFEs here,
using the dedicated issue templates.
* [Crane Runner Github](https://github.com/konveyor/crane-runner)

## Prerequisites

* We recommend bringing a RHEL-family machine (Fedora 35, Centos 8, RHEL 8) with
podman installed. A VM should work fine. You'll also need [minikube](https://minikube.sigs.k8s.io/docs/start/) available. It's convenient to just
use the podman driver for minikube; it's lightweight and works great. We have
some helper scripts that you will use to spawn a couple of minikube clusters
to migrate between (let's call them src, dest), and we'll also set up some
iptables network forwarding rules along with some in-cluster dns to ensure the clusters
can route traffic to one another, and are able to resolve ingress. We also have
scripts to help clean this up.

* NOTE: We also have had folks run through the scenarios on Mac machines, but
fair warning, this path has significantly less usage.

* Have [jq](https://github.com/stedolan/jq) installed on your system and available
inside of your path.

## Some background

Crane itself is a cli tool that's designed to help users with application
portability. It is designed with the unix philosophy in mind, meaning that you
could consider it a swiss-army knife of tightly focused and sharp tools that
are intended to work in conjunction with one another to achieve more sophisticated
things. It can be used directly on your working machine, and uses a standard
kube config to communicate with your clusters, accepting a kube context specification
to understand the coordinates to the cluster you're trying to operate upon.

Because of its "pipelined" nature, it pairs very nicely with Tekton (OpenShift pipelines).
We are working on a product that we expect to be shipped sometime in the Spring
of 2022 that is installable via operator, augments the OpenShift console directly,
and exposes a nice UI for driving migrations. Under the covers, it will depend
upon OpenShift Pipelines, and will use crane to migrate applications around.
Crane will execute its tasks within a pipeline, embedded inside of an image.
That image and the associated Tekton assets that help you run pipelines to
do useful things is called [crane-runner](https://github.com/konveyor/crane-runner).

During this hackfest, we'll use crane-runner and these Tekton tasks to run
crane within your cluster, and execute migrations.

## Scenarios

We have added several examples to crane-runner that gradually ratchet up the
complexity of the overall scenario, and demonstrate the value of crane with
one possible usage of the tool. Again, because it is a toolbox of utilities,
it's extremely flexible in what it can do.

Our scenario instructions can be found in our [crane-runner examples](https://github.com/konveyor/crane-runner/tree/main/examples).

## Support and filing bugs

Please join the #konveyor channel in [Kubernetes slack](https://k8s.slack.com/) for support and
discussion. We have an issue template in the crane-runner repo that can be
used specifically for the hackathon as well as an RFE template for suggested enhancements.
If your issue is not specific to crane-runner and the tasks, but the crane tool
itself, please consider filing it in the [crane repo](https://github.com/konveyor/crane).

Thank you for attending!
