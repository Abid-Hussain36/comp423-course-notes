# Setting up a Dev Container for Go

* Primary author: [Abid Hussain](https://github.com/Abid-Hussain36)
* Reviewer: [William Millen](https://github.com/wvmillen)

## Prerequisites
* **GitHub Account**, which you can Create [here](https://github.com)
* **Git**, which you can Download [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* **VS Code**, which you can Download [here](https://code.visualstudio.com)
* **Docker**, which you can Download [here](https://www.docker.com/products/docker-desktop)
* **Basic Command Line Knowledge**


## Creating your Local Repository
Creating a local repository would allow you to systematically track changes made to your project over time, represented as commits, and rollback to previous versions if needed. This offers you a great deal of flexibility in experimenting with different features on your codebase.

1. Open your Terminal
2. cd into your Desired Parent Directory
3. Create a New Directory and cd into it:
``` bash
mkdir go-project
cd go-project
```
4. Initialize a New Git Repository
``` bash
git init
```
5. Add a README File and Commit it
``` bash
echo "# Go Project" > README.md
git add README.md
git commit -m "Initial Commit"
```

## Creating your Remote Repository
Creating a remote repository allows you to share the commits (read: changes) you have made on your local repository to a repository hosted on the cloud which other people can use as well. This allows you to collaborate with other developers on a project seamlessly, enabling you to add new functionalities through pushes to this remote repository.

1. Login into your GitHub Account
2. Create a New Repository by Setting:
    * Name: The Name of your Repository. Set this to `go-project`
    * Description: A Description of your Repository
    * Visibility: Who is Permitted to View your Repository. Set this to `public`

    !!! Note
        Make sure to only edit these properties.

3. Copy the HTTP Link to your Repository

## Linking your Local and Remote Repositories
Linking your local repository to your remote repository allows you to upload the commits you have made on your local repository to the remote repository for your collegues to see.

1. In your Terminal, within your Local Repository's Directory, Add your GitHub Repository as a Remote, with the Alias of Origin:
``` bash
git remote add origin https://github.com/<your-gh-username>/go-project.git
```
2. Check your Local Branches:
``` bash
git branch
```

    !!! Note
        If you find that a branch named `master` exists instead of `main`, rename it: `git branch -M main`

3. Push your Local Commits to your Remote Repository:
``` bash
git push --set-upstream origin main
```

## Creating your Dev Container
A development container is essentially an isolated enviornment that is created on your computer which has certain dependencies preinstalled and preconfigured. This is useful because it allows you and your teammates to work with the exact same dependencies in your project, eliminating errors caused by differing dependencies and their versions installed on your and your teammates' host machines.

1. In the Terminal, within your Go Project Directory, Open the Directory in VS Code:
``` bash
code .
```
2. If you haven't already, Install the Dev Containers Extension for VS Code
3. Create a `.devcontainer` in your Project's Root Directory
4. Within the `.devcontainer` Directory, Create a File Named `devcontainer.json`
5. Configure your Dev Container with the Following Details:
``` yaml
{
  "name": "COMP423 Course Notes",
  "image": "mcr.microsoft.com/devcontainers/python:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["golang.go"]
    }
  },
  "postCreateCommand": ""
}
```

    !!! Note
        * Name: A name for your container
        * Image: The Docker image for your container
        * Customizations: Adds configurations, such as installing extensions for VS Code automatically
        * postCreateCommand: Defines a command to run after the container is created

6. Reopen your Project in a Dev Container by Pressing `Ctrl + Shift + P` or `Cmd + Shift + P` and then Typing and Running the Command: `Dev Containers: Reopen in Container`

## Writing "Hello World" in Go
Go is a statically typed, compiled language that was developed by Google. It is loved for its high performance, simplicity, and concurrency support. Go is widely used for developing server-side applications, CLI tools, distributed systems and microservices, real-time systems, and high performance systems.

1. Create a New Terminal in VS Code and Check your Go Version:
``` bash
go version
```
2. Create a Directory for your Go Code and cd into it:
``` bash
mkdir hello-world
cd hello-world
```
3. Create a New Go Module for your Directory to Keep Track of Needed Dependencies from Other Modules:
``` bash
go mod init hello-world
```
4. Create a New Go File to Write your Code:
``` bash
touch hello-world.go
```
5. Write your Hello World Program:
``` go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```
6. Compile and Execute your Hello World Program:
``` bash
go run hello-world.go
```

!!! Note
    You could have alternatively used the `go build hello-world.go` command. This command compiles your program into an executable object file, much like the `gcc` command which compiles C programs. After your go executable is created, you can run it with the command `./hello-world`.

7. Push your Changes to Github
``` bash
git add .
git commit -m "Wrote Hello World in Go"
git push origin main
```

8. Congratulations!!!
You now know how to setup local and remote repositories, how to link them together, how to create a dev container, and how to configure it to run programs in Go!