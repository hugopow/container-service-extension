# container-service-extension

Use at your own risk. No support is provided. This is not an official CSE feature or release.

What is Container Service Extension?

You can read that here https://vmware.github.io/container-service-extension/cse3_1/INTRO.html. The problem with CSE is that it is quite difficult to install. You can read up on one of my previous posts here https://vmwire.com/2021/10/14/install-container-service-extension-3-1-1-with-vcd-10-3-1/, where I described the step by step process to install CSE into a Virtual Machine.

CSE is also not available as an OVA (Virtual Appliance), so some users may find it difficult to install and configure as you need Linux knowledge.

What Problems does this Helm chart solve?

This helm chart can be used to configure, install and run CSE 3.1.2 on a Kubernetes cluster. The config and deployment is very simple and takes less than 5 minutes to get up and running.

You can also run multiple pods of CSE to enable high availability with RabbitMQ. Unsupported but it works.

Installation Instructions

The configuration and installation is a very simple process:

    Download the helm chart from my Github repository or from my Harbor registry
    Unzip it locally
    Make changes to the helm chart values.yaml
    Make changes to the config-not-encrypted.yaml which contains the CSE configuration
    Make any optional changes to the run-cse.sh script, to comment out sections as necessary.
    Package your changes to a new helm chart and upload to your repository
    Install the helm chart with a single command such as

helm install cse oci://harbor.vmwire.com/container-service-extension --version 0.2.0 -n container-service-extension -f /home/container-service-extension/values.yaml

Don't forget to download the photon-cse image from my Harbor registry to save bandwidth, both yours and mine. (big grin).

Pull commands to download the bits helm pull oci://harbor.vmwire.com/library/container-service-extension

this pulls this helm chart. docker pull harbor.vmwire.com/library/photon-cse

this pulls the photon-cse image which is a Photon 3.0 image with the necessary per-requisites to run CSE.

Push commands to push to your repository helm push cse-0.1.0.tgz oci://<your-registry/

docker tag photon-cse /library/photon-cse:latest docker push /library/photon-cse:latest
