# Lab 1: Course Infrastructure Setup

During this course, you will become familiar with several popular and industry-relevant software engineering tools, including an IDE, build systems, and automated style checkers for both Java and TypeScript. In this lab, you will set up your environment and explore some tools for getting started with TypeScript. The instructions are unusually long, because we try to provide more detailed help for common problems. If you encounter problems along the way, look back at the instructions, work through problems with others, and seek help from the TAs during the lab session. 



## Deliverables

- [ ] Locally clone your 214 Git repository, fix a typo in the `README.md` file ("assigment" -> "assignment") and commit and push the change.
- [ ] Install node.js, TypeScript, and an editor/IDE of your choice. Show that you can compile and run the TypeScript starter code of homework 1 on your machine.
- [ ] Install Java 17, maven, and an IDE of your choice. Run `java --version` to verify it is version 17. Show that you can compile and run the Java starter code of homework 1 on your machine.



## Setting Up Your Repo 

In this lab, we will work with the starter code from homework 1. Each student in 17-214/514 is assigned a GitHub repo per homework assignment. You can create it by following the GitHub Classroom link in the description of [Homework 1 on Canvas](https://canvas.cmu.edu/courses/35846/assignments/607925).

- If you do not have *git* yet, follow the [download instructions](https://git-scm.com/downloads).
- If you do not have a *GitHub* account yet, [create one](https://github.com/). 
- Follow the GitHub classroom link on Canvas/Piazza to create your own GitHub repository with the starter code for homework 1.

**Setting up your Personal Access Token.** Before cloning the repository, you should set up your own personal access token; otherwise, you might get an invalid username or password error. GitHub removes these every year, so even if you have made one in the past, you may need to recreate it. You can follow the [instructions](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) for the general outline on how and where to create a personal access token. Some things to note: 

- You can name it something like 17214f23 or whatever you’d like 
- Set the expiration date to be some time past the end of the semester (e.g. 12/21/23), so that you don’t have to remake it again this semester 
- You can select all of the options if you’d like and read more about what they do [here](https://docs.github.com/en/developers/apps/building-oauth-apps/scopes-for-oauth-apps). At the very least, make sure you have the **repo, workflow, user, project** scopes selected. 
- **Important:** Once you generate the token, make sure you save it somewhere safe and accessible to you before you leave the page. You will need to use it as your password to log-in and you won’t be able to see it again after leaving the page. 

**Cloning the Repository.** Navigate to your own remote repository, and then click on the green “code” button to copy the URL of this remote repository so that you can clone it. 

We recommend to learn to use *git* on the command line, but you can also the integration in your IDE or [GitHub Desktop](https://desktop.github.com/). To clone the repository from the command line run the following in a terminal: `git clone <The URL of the remote repository>`

This will download the entire repository to your computer. If you are prompted to input your username and password, make sure that you use your personal access token you created above as the password. 

## TypeScript Tools

To run JavaScript applications outside the browser we use Node.js. We write TypeScript code that gets compiled into JavaScript.

### Installing Node.js, npm, and TypeScript

Follow [instructions](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) to install Node.js on your system. We recommend you install it through [nvm](https://github.com/nvm-sh/nvm). If you’re working on a Windows machine, we recommend using [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) for installing nvm (and subsequently using WSL for all development in this class). 

The following command will automatically download the installation script and update your environment to install it: `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash`  Verify it installed correctly by running: 

`command -v nvm`, which should output nvm.

With nvm installed, you can then install Node.js. Run the command `nvm install node` which should install the latest version of node. Then, run `nvm install-latest-npm` which should install the latest version of npm supported by the node version you installed.

**Package management with npm.** We are using npm for package management:

- The `package.json` file is the configuration file, which lists dependencies and commands
- `npm install` installs all dependencies and puts them in a local directory `node_modules`, which should *not* be committed to version control and is automatically in the search path for imports from JS/TS code
- The `package.json` file has a `dev-dependencies` section, which are development tools not needed at runtime, such as test execution, compilers, and style checkers.
- `npm install -g X` installs package X globally, so not just for the current directory. This is often useful for tools like TypeScript that are installed through npm. `npx` is a useful tool for executing a tool installed locally and hence not otherwise in the path, like `npx tsc`.
- The `package.json` file has a `scripts` section, which is just a way to describe command line instructions that can be easily run with `npm run X` from the command line. These are just convenient shorthands.

*Checkpoint:* Run npm install to install dependencies and tools locally. You can find them in the `node_modules` folder if you are interested. 

**Installing TypeScript.** To install TypeScript run `npm install -g typescript` and afterward `tsc` should be available on your command line. (The project we provide already sets up TypeScript, so `npm install` should already install TypeScript locally).

*Checkpoint:* Confirm that `tsc --version` works in your working directory (or `npx tsc --version` if you installed it only locally).

Run `tsc` to compile the TypeScript code. You can find the output in the dist/ directory.

### VSCode for TypeScript

VSCode is a popular IDE for TypeScript which we recommend for this course. It works for TypeScript out of the box, no further set up needed. 

Install VSCode following [instructions](https://code.visualstudio.com/) on its homepage or use your operating system's package manager.

*Checkpoint:* You can explore the source files of the cloned repository in the IDE.

**Running a Program in VSCode.** VSCode executes code in the debugger by default. Select “Start debugging” from the menu and confirm to use node.js as the runtime. Note that the program will fail because the debugger does not support command line input, but everything until this part will execute.

If you just want to run the code use a terminal or the built-in terminal in VSCode (“New Terminal”) and run `node dist/index.js` to start the compiled program (or `npm run start` for the preconfigured run script in package.json)

### Style checking with ts-standard

Linters check your code against a style-guide that specifies some good coding conventions (and sometimes annoying nitpicky things). Linters automates the process of checking for common style flaws such as the use of magic numbers. We preconfigured the project with the (very picky) style checker *ts-standard*. It comes preconfigured in the project with `npm run lint` or just run it with `npx ts-standard` (or just `ts-standard` if you installed the package globally). It has a fix option `npx ts-standard --fix` that will automatically fix many issues, which can be very useful. To integrate ts-standard into vscode, install the *StandardJS* extension and in the settings pick ts-standard as the engine.

*Checkpoint:* Install and configure the StandardJS extension. Introduce some style violation to see what it reports (like extra or missing whitespace). Try to fix it automatically with “npx ts-standard --fix”.



## Java Setup

### Installing Java 

Download and install Java 17. The language used in this class is Java 17. Several vendors provide implementations of Java 17, if in doubt choose the open-source OpenJDK 17. 

Installing the right version of Java can sometimes be a bit tricky. If you already use a package manager for your platform (homebrew, apt, snap, scoop, etc) installing Java with that tool is probably the easiest. Below are detailed instructions, but feel free to skim/skip.

*Note for Windows users:* We recommend installing [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) (Windows Subsystem for Linux) and using it for all your development environments installations and future assignments when following this guide. 

**Installing Java using homebrew on MacOS.** Run `brew install openjdk@17` and run the command from the output to create a symbolic link. See [these instructions](https://medium.com/@manvendrapsingh/installing-many-jdk-versions-on-macos-dfc177bc8c2b) for a detailed reference.

**Manual installation and other operating systems.** 

- MacOS. Download the MacOS tar.gz archive from the [OpenJDK website](https://jdk.java.net/archive/). Untar the archive (double click), and move the contained directory (named something like jdk-17.0.2.jdk) to the /Library/Java/JavaVirtualMachines/ directory
- Linux. If possible, please really use the package manager of your distribution. It will be much easier.
- Windows. To install OpenJDK, download the Windows zip file from the [OpenJDK website](https://jdk.java.net/java-se-ri/17), and follow the instructions at [this StackOverflow post ](https://stackoverflow.com/questions/52511778/how-to-install-openjdk-11-on-windows/52531093#52531093)to correctly set Windows environment variables. Alternatively, if you wish to just use an install wizard, [download and install the Oracle JDK](https://www.oracle.com/java/technologies/javase-jdk16-downloads.html).

**Managing multiple Java installations.** If you already have existing different versions of Java installed and want to keep them, you can use [jEnv](http://jenv.be) to help manage your installations. As another option, you can set the JAVA_HOME environment variable in your ~/.zshrc or ~/.bash_profile or Windows configuration to point to Java 17 folder (e.g., `export JAVA_HOME=$(/usr/libexec/java_home -v17)`; if you choose this approach, you’ll need to modify the number that comes after -v if you ever want to switch your Java version). If you’re interested in switching between Java versions (not needed in this course), see [here](https://medium.com/@manvendrapsingh/installing-many-jdk-versions-on-macos-dfc177bc8c2b) under the section “Switching JDKs” for instructions on how to do so. 

*Checkpoint:* Confirm your Java installation by inspecting the output of the command `java -version` and `javac -version`. You should see something similar to: *openjdk version "17.0.2" 2022-01-18.* The major version should be 17, any vendor and patch version is okay. 

### Installing Maven

We use Maven as the build tool and package manager for Java in this course. Install a recent version of Maven. You can follow the instructions in [this link](https://www.baeldung.com/install-maven-on-windows-linux-mac) and verify that Maven 3.8.7 or newer is installed.[^1] More information about Maven can be found [here](https://maven.apache.org/what-is-maven.html).

For Mac users, you might find it easiest to install maven using homebrew: `brew install maven`

Explore the `pom.xml` file to see how the project is currently configured.

*Checkpoint:* In your local directory, try to run `mvn install` which will download dependencies and compile the code. You can either type `mvn install` in the terminal or click the Maven tab on the bottom left, scroll down to “install” and press the triangle.

### VSCode for Java

VSCode supports also Java. We recommend VSCode for development in both Java and TypeScript, but you are free to chose others. While IntelliJ and Eclipse are more advanced if you are solely developing in Java, using VSCode for both will save you from having to switch between IDEs which can be tedious. 

**Navigate to the sidebar and look for the extensions symbol (5th from the top) and search for “Extension Pack for Java” and install it locally**. This extension includes linting, test running and debugging, support for Maven (the build automation tool we use for Java projects in this class), and a few other helpful extensions. 

You need to have Java 17 installed for this project. Do not downgrade your Java version if you are asked to, this will break your project. 

*Checkpoint:* You can explore the source files in the IDE.

**Running a Java program in VSCode.** Once you have successfully opened the project and installed Maven, you should be able to view all the starter source files. Try building the program and run the main class.



![img](figures/vscode-run.png)

To run a program go to the Main class (`Main.java`), you should see a *Run | Debug* prompt above the main method. Click *Run*. You will be able to view the run result at the bottom. You can interact with this program by replying on the console and hitting “enter”.

Alternatively, you can open the `Main.java` file and then open the *Run and Debug* tab on the left sidebar (4th from the top). Pressing Run and Debug will have the same effect as pressing Debug on the prompt above the main method. 

**Passing a command-line argument (you might find this helpful for HW1).** If you want to pass an argument to the program from within VSCode, click *“Create a launch.json file”*. This will open a file containing all of the run configurations. If you’d like to modify this in the future, you can find it in the .vscode folder. 

![img](figures/vscode-launchconfig.png)

Under the configuration named `Launch Main`, you can add the attribute `args` and supply it with your arguments. For example `"args": "--help"`.  You can also supply multiple arguments in the same line: `"args": ["--arg1", "value1", "--arg2", "value2", …]`

For more information on launch configurations and Java debugging in VSCode, see [here](https://code.visualstudio.com/docs/editor/debugging#_launch-configurations).

### Checkstyle for Java

We preconfigured the project with the style checker *CheckStyle*. It is automatically executed as part of compiling and packaging the project with `mvn site (on the command line or in the IDE).

If you’d like to be able to run checkstyle through VSCode’s UI, you can search for and install the [“Checkstyle for Java” extension](https://code.visualstudio.com/docs/java/java-linting#_checkstyle).  To use this extension: Right click the `checkstyle.xml` file and select *“Set the Checkstyle Configuration File”* . Then right click on the file you want to check and select *“Check Code with Checkstyle”*. You can view the checkstyle violations on the problems tab near your terminal. 

*Checkpoint*: Test Checkstyle by renaming one method to start with a capital letter (against Java's style guidelines) and it should complain. A neat thing that this plugin does is automatically lint your code as you write it. You can test this out by opening the “problems” tab and making further changes.



## Turning in Your Work

For finishing this lab (and all homeworks), you are required to submit your work by pushing changes to your repositories on GitHub. 

The minimal instructions to submit code with Git on the command line are:

````bash
git add <filename1> <filename2>
git commit -m "<some message>"
git push
````

**git add** adds files to the staging area, **git commit** saves everything on the staging area along with the given commit message, and **git push** records local commits to the remote repository. After pushing changes you should see them on GitHub.

If you are new to Git you will learn to better use it throughout the semester, including best practices and more advanced functionality like branches. We provide more detailed instructions in a [separate document](git-basics.md) but encourage you to find documentation and tutorials on your own too.





[^1]: If you choose to use the instructions linked, the `chown -R root:wheel Downloads/apache-maven*` command should actually be `sudo chown -R root:wheel Downloads/apache-maven*`. If you run into issues with adding Maven to your environment path, try using `~/.zshrc` instead of `~/.zshenv`.
