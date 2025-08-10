## Terraform Brain Dump

I did some starter tutorials on [Hashicorp's Dev Site] (https://developer.hashicorp.com/terraform/tutorials/). I love that they have a sim you can use to push out commands and test it out without the need of an **aws** env. Things learned (I use learned very liberally, I basically followed guides and used ChatGPT for help at times): 

- You can make a terraform.tf file that has the configuration for terraform itself. It's called a terraform block (usually named **teraform.tf**) . It seems like you can have it at the top of your **main.tf** but the tutorial shows it as a separate file. The **main.tf** has the configuration of the infrastructure. For my learning, I'm using an AWS free account. So the config would look something like what's on tutorial: 


```
provider "aws" {
  region = "us-west-2"
}

data "aws_ami" "ubuntu" {
  most_recent = true

  filter {
    name = "name"
    values = ["ubuntu/images/hvm-ssd-gp3/ubuntu-noble-24.04-amd64-server-*"]
  }

  owners = ["099720109477"] # Canonical
}

resource "aws_instance" "app_server" {
  ami           = data.aws_ami.ubuntu.id
  instance_type = "t2.micro"

  tags = {
    Name = "learn-terraform"
  }
}
```

### Commands I learned

1. **terraform fmt** automatically puts the tf files in the format that Hashicorp recommends. 
2. **terrafrom init** to initialize the terraform workspace
3. **terraform validate** to make sure you have a valid config set up
4. **terraform apply** pushes out the configuration to the api of the chosen provider (in this case AWS)
5. **terraform destroy** to destroy the configuration inside of the chose provider. So no headache on manually destroying infra as needed which is awesome. 

## git/Github TIL:

The fact that I struggled to understand what git and Github were and what they were used for just a few days ago is humbling. I'm not coming from a dev background so it's all so new to me! I think I finally got a grasp on it though. I just forced myself to make folders on my macbook and create a repo on Github and push the folders and files to it so I could understand the git commands, and how they (**Github & git**) both interact with eachother. 

Essentially git it used for versioning purposes. It's basiclaly so I can revert back to a previous state of the code or writing in case I messed something up. And then you sync your files from your client to GitHub for various reasons. Like sharing code, backing up your data to the cloud, or collaborating with other people at a company on a project. I've gotten used to creating branches so I'm not just pushing to main so I can use best practices now for when I work somewhere that requires it. I used [codeacademy ](https://www.codecademy.com/) to work through lessons on git and GH as well and I recommend that for beginniners. 

### Commands I used often this week

1. **git config** to set things up and configure my username and email so that way when I push to GH it's tagged to my account as a contribution. This was super confusing at first. And it's really hard to work with multiple GH accounts from the client. Like a real pita. 
2. **git init** makes the cd (current directory) a Git repo. 
3. **git status** shows modified files in the directory staged for commit
4.** git add** adds the files to staging 
5. **git commit** -m "" for when you're commiting the changes to staging 
6. **git push** is to sync local changes to your GH repo 
7. **git branch** creates a new branch at the current commit
8. **git checkout** is what you use to switch to another branch and check it out in your working directory. 
9. **git log** is a log of previous commits in that branch



