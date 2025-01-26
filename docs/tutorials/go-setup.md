# Setting up a Dev Container for Go

* Primary author: [Abid Hussain](https://github.com/Abid-Hussain36)
* Reviewer: [William Millen](https://github.com/wvmillen)

## Prerequisites
* **GitHub Account**
* **Git**
* **VS Code**
* **Docker**


## Creating your Local Repository
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
git add README.md
git commit -m "Initial Commit"
```

## Creating your Remote Repository
1. Login into your GitHub Account
2. Create a New Repository by Setting:
    * Name: The Name of your Repository. Set this to `go-project`
    * Description: A Description of your Repository
    * Visibility: Who is Permitted to View your Repository. Set this to `public`

    !!! Note
        Make sure to only edit these properties.

3. Copy the HTTP Link to your Repository

## Linking your Local and Remote Repositories
1. In your Terminal, within your Local Repository's Directory, Add your GitHub Repository as a Remote, with the Alias of Origin:
``` bash
git remote add origin https://github.com/<your-gh-username>/go-project
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
1. Check your Go Version:
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