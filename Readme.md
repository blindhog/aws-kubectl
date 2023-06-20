# eks-kubctl
The purpose of the `eks-kubectl` repo is to create a docker container for kubctl to manage k8s clusters in EKS for multiple environments.

# Documentation References
[Amazon Install kubectl documentation](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)
[Amazon Install eksctl documentation](https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html)
[Amazon Install AWS CLI documentation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

# Build Docker Images
1.  Navigate to the `amd64` or `arm64` directory according to your CPU architecture.
    ```
    cd $(uname -m)
    ```
2.  Use the following docker command to build the eks docker container
    ```
    docker build -t aws-kubectl:latest .
    ```
3.  Use the following docker command to run the eks docker container.
    ```
    docker run --rm -it -v ~/.aws:/root/.aws aws-kubectl:latest bash
    ```
4. Configure aws cli. Enter your `Access key ID` and `Secret Access Key`
    ```
    aws configure
    ```
    Sample:
    ```
    root@9773b5acae26:/# aws configure
    AWS Access Key ID [****************7DV5]: 
    AWS Secret Access Key [****************izi3]: 
    Default region name [us-east-2]: 
    Default output format [json]: 
    ```
5. Update k8s config
    ```
    aws eks update-kubeconfig --name example
    ```
6. Run kubectl commands
   ```
   kubectl get pods --name example