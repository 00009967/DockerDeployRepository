| Language | Platform | Author |
| -------- | --------|--------|
| HTML |  Azure Web App, Virtual Machine| |



# Sample HTML website 

Sample HTML/CSS web app that you can deploy to Azure. 

## License

See [LICENSE](LICENSE).


## Contributing
This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

#!/bin/bash
sudo yum update -y
sudo yum install -y docker
sudo service docker start
sudo yum install -y git
mkdir website
cd website
git init
git remote add origin https://github.com/wiuttutor/DockerDeployRepository.git
git pull origin main
sudo usermod -a -G docker ec2-user
docker build -t webserver-image:v1 .
docker run -d -p 80:80 webserver-image:v1
