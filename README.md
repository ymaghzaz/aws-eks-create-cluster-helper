# aws-eks-create-cluster-helper

## step1: Install and Configure kubectl 
  The kubectl binary is available in many operating system package managers, and this option is often much easier than a manual download and install process. You can follow the instructions for your specific operating system or package manager in the Kubernetes documentation to install (https://kubernetes.io/docs/tasks/tools/install-kubectl/).

## step2: install aws-iam-authenticator for Amazon EKS

Download the Amazon EKS-vended aws-iam-authenticator binary from Amazon S3:

Linux: https://amazon-eks.s3-us-west-2.amazonaws.com/1.12.7/2019-03-27/bin/linux/amd64/aws-iam-authenticator

MacOS: https://amazon-eks.s3-us-west-2.amazonaws.com/1.12.7/2019-03-27/bin/darwin/amd64/aws-iam-authenticator

Windows: https://amazon-eks.s3-us-west-2.amazonaws.com/1.12.7/2019-03-27/bin/windows/amd64/aws-iam-authenticator.exe

```js
curl -o aws-iam-authenticator https://amazon-eks.s3-us-west-2.amazonaws.com/1.12.7/2019-03-27/bin/darwin/amd64/aws-iam-authenticator
```

Apply execute permissions to the binary.

```js
chmod +x ./aws-iam-authenticator
```
Copy the binary to a folder in your $PATH. We recommend creating a $HOME/bin/aws-iam-authenticator and ensuring that $HOME/bin comes first in your $PATH.
```js
mkdir $HOME/bin && cp ./aws-iam-authenticator $HOME/bin/aws-iam-authenticator && export PATH=$HOME/bin:$PATH
```
Add $HOME/bin to your PATH environment variable.

- For Bash shells on macOS:
```js
mkdir $HOME/bin && cp ./aws-iam-authenticator $HOME/bin/aws-iam-authenticator && export PATH=$HOME/bin:$PATH
```
- For Bash shells on Linux:

```js
echo 'export PATH=$HOME/bin:$PATH' >> ~/.bashrc
```
Test that the aws-iam-authenticator binary works.
```js
aws-iam-authenticator help
```

## step3: install eksctl cli : eksctl is a simple CLI tool for creating clusters on EKS https://eksctl.io/


To download the latest release, run:
```js
curl --silent --location "https://github.com/weaveworks/eksctl/releases/download/latest_release/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
```


Alternatively, macOS users can use Homebrew:
```js
brew tap weaveworks/tap
brew install weaveworks/tap/eksctl
```
and Windows users can use chocolatey:
Alternatively, macOS users can use Homebrew:
```js
chocolatey install eksctl
```

