# Docker Learning Journey 🐳

A comprehensive guide documenting my Docker learning experience, from basic concepts to practical implementation.

## Overview

This repository documents my hands-on journey learning Docker and containerization. Through this learning process, I:

- Created my first Docker image using a simple Node.js application (**hello-docker**)
- Practiced essential Linux commands inside an Ubuntu container
- Learned Docker fundamentals including images, containers, and Dockerfiles
- Gained experience with Docker CLI commands and container management
- Explored the Linux file system and command-line operations

This README serves as both a learning log and a reference guide for Docker and Linux fundamentals.

## What is Docker?

Docker is a containerization platform that allows us to package our code and dependencies into isolated containers. It enables developers to build, ship, and run applications consistently across different environments.

### Key Benefits
- **Consistency**: Eliminates "works on my machine" problems
- **Isolation**: Applications run in isolated environments
- **Portability**: Run the same container on any system
- **Efficiency**: Lightweight compared to virtual machines
- **Scalability**: Easy to scale applications horizontally

## What is a Container?

A **container** is an isolated environment for running an application. It is a lightweight, executable package of software that includes everything needed to run an application:
- Application code
- Runtime environment
- System tools
- System libraries
- Settings and configurations

Containers are isolated from each other and from the host system, ensuring applications run consistently regardless of where they are deployed.

## What is a Dockerfile?

A **Dockerfile** is a text file that contains instructions for packaging an application into an image. It defines:
- The base operating system or runtime
- What files to copy into the image
- What dependencies to install
- What commands to run
- How the application should start

Think of it as a recipe that Docker follows to build your application image.

## Virtual Machines vs Containers

### Virtual Machines
- Include full operating system
- Heavy resource usage (GBs)
- Slow startup (minutes)
- Complete isolation

### Containers
- Share host OS kernel
- Lightweight (MBs)
- Fast startup (seconds)
- Process-level isolation
- More efficient resource utilization

**Analogy**: VMs are like separate houses with their own utilities, while containers are like apartments in a building sharing infrastructure.

## Docker Architecture

Docker uses a client-server architecture:

```
┌──────────────┐
│ Docker Client│
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ Docker Daemon│
└──────┬───────┘
       │
       ▼
┌──────────────┐
│   Containers │
└──────────────┘
```

### Components
- **Docker Client**: CLI tool to interact with Docker
- **Docker Daemon**: Background service managing containers
- **Docker Images**: Read-only templates for containers
- **Docker Containers**: Running instances of images
- **Docker Registry**: Storage for Docker images (Docker Hub)

## Installing Docker

I installed Docker Desktop from the official Docker website. After installation, I also:

1. Installed Ubuntu from the Windows Store
2. Enabled WSL (Windows Subsystem for Linux) integration in Docker Desktop
3. Configured Ubuntu under **Resources → WSL Integration** in the Docker app

This setup allows me to run Docker commands directly from Ubuntu terminal on Windows.

## Development Workflow

1. **Write Dockerfile**: Define your application environment
2. **Build Image**: Create an image from Dockerfile
3. **Run Container**: Start a container from the image
4. **Test & Debug**: Verify application works correctly
5. **Push to Registry**: Share image on Docker Hub
6. **Deploy**: Pull and run on production servers

## Docker in Action

### Basic Docker Commands

```bash
# Pull an image from Docker Hub
docker pull <image-name>

# List all images
docker images

# Run a container
docker run <image-name>

# Run container interactively
docker run -it <image-name>

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a container
docker stop <container-id>

# Remove a container
docker rm <container-id>

# Remove an image
docker rmi <image-id>

# Build an image from Dockerfile
docker build -t <image-name> .

# Execute command in running container
docker exec -it <container-id> <command>
```

## The Linux Command Line

### Linux Distributions

Popular distributions:
- **Ubuntu**: User-friendly, great for beginners
- **Debian**: Stable and reliable
- **Alpine**: Minimal, perfect for containers
- **CentOS/RHEL**: Enterprise-focused
- **Fedora**: Cutting-edge features

### Running Linux

```bash
# Run Ubuntu container interactively
docker run -it ubuntu

# Run Ubuntu with terminal access
docker run -it ubuntu bash
```

### Managing Packages

#### Ubuntu/Debian (APT)
```bash
# Update package list
apt update

# Install package
apt install <package-name>

# Remove package
apt remove <package-name>

# List installed packages
apt list --installed
```

#### Alpine (APK)
```bash
# Update package index
apk update

# Install package
apk add <package-name>

# Remove package
apk del <package-name>
```

### Linux File System

```
/                    (root directory)
├── bin             (essential binaries)
├── boot            (boot loader files)
├── dev             (device files)
├── etc             (configuration files)
├── home            (user home directories)
├── lib             (shared libraries)
├── opt             (optional software)
├── root            (root user home)
├── tmp             (temporary files)
├── usr             (user programs)
└── var             (variable data)
```

### Navigating the File System

```bash
# Print working directory
pwd

# List files and directories
ls
ls -l      # Long format
ls -a      # Show hidden files
ls -lh     # Human-readable sizes

# Change directory
cd /path/to/directory
cd ..      # Go up one level
cd ~       # Go to home directory
cd -       # Go to previous directory
```

### Manipulating Files and Directories

```bash
# Create directory
mkdir directory-name
mkdir -p parent/child/grandchild  # Create nested directories

# Create file
touch filename.txt

# Copy files
cp source.txt destination.txt
cp -r source-dir/ destination-dir/  # Copy directory recursively

# Move/Rename files
mv oldname.txt newname.txt
mv file.txt /path/to/destination/

# Remove files
rm file.txt
rm -r directory/     # Remove directory recursively
rm -rf directory/    # Force remove without prompts

# View file contents
cat file.txt         # Display entire file
less file.txt        # View file page by page
head file.txt        # Show first 10 lines
tail file.txt        # Show last 10 lines
tail -f log.txt      # Follow file updates (useful for logs)
```

### Editing and Viewing Files

#### Nano (Beginner-friendly)
```bash
nano filename.txt
# Ctrl+O to save, Ctrl+X to exit
```

#### Vim (Advanced)
```bash
vim filename.txt
# Press 'i' for insert mode
# Press 'Esc' then ':wq' to save and quit
# Press 'Esc' then ':q!' to quit without saving
```

### Redirection

```bash
# Redirect output to file (overwrite)
echo "Hello" > file.txt

# Append output to file
echo "World" >> file.txt

# Redirect input from file
sort < unsorted.txt

# Chain commands with pipe
cat file.txt | grep "search-term" | sort

# Redirect errors
command 2> error.log

# Redirect both output and errors
command > output.log 2>&1
```

## My Practice Projects

### 1. Hello Docker - Simple Node.js Application

In this project, I created my first custom Docker image from scratch. I built a simple Node.js application that prints "Hello Docker!" and packaged it into a Docker container. This exercise taught me:

- How to write a Dockerfile with instructions for building an image
- The process of building a Docker image using `docker build`
- How to run containers from custom images
- The basic structure of containerizing a Node.js application

This hands-on project helped me understand the complete workflow of creating and running containerized applications.

#### Files Structure
```
hello-docker/
├── app.js
├── Dockerfile
└── README.md
```

#### app.js
```javascript
console.log("Hello Docker!")
```

#### Dockerfile
```dockerfile
FROM node:alpine
COPY . /app
WORKDIR /app
CMD node app.js
```

#### Build and Run
```bash
# Build the image
docker build -t hello-docker .

# Run the container
docker run hello-docker

# Output: Hello Docker!
```

### 2. Ubuntu Practice

In this practice session, I pulled the official Ubuntu image from Docker Hub and ran it interactively to explore Linux commands. I gained hands-on experience with:

- Managing Docker containers (`docker ps`, `docker ps -a`)
- Installing packages using APT package manager
- Creating and manipulating files and directories
- Editing files with nano text editor
- Viewing file contents using various tools (cat, more, less, head, tail)
- Understanding output redirection and file operations
- Navigating the Linux file system

This practice gave me essential Linux command-line skills that are crucial for working with containers and servers.

```bash
# Pull Ubuntu image from Docker Hub
docker pull ubuntu

# Run Ubuntu container interactively
docker run -it ubuntu

# Run Ubuntu with bash shell
docker run -it ubuntu bash
```

#### Container Management Commands Practiced
```bash
# List running containers
docker ps

# List all containers (including stopped ones)
docker ps -a
```

#### Package Management
```bash
# Update package lists
apt update

# Install text editors
apt install nano
apt install less
```

#### File and Directory Operations

**Creating Files and Directories:**
```bash
# Create a directory
mkdir directoryname

# Create an empty file
touch filename
```

**Editing Files:**
```bash
# Edit file with nano
nano filename
# Ctrl+O to save, Ctrl+X to exit
```

**Removing Files and Directories:**
```bash
# Remove a single file
rm filename

# Remove multiple files
rm filename1 filename2

# Remove directory recursively
rm -r directoryname
```

**Moving and Renaming:**
```bash
# Rename a file
mv oldfilename newfilename

# Move file to another location
mv filename /etc
```

#### Viewing File Contents

```bash
# Display entire file content
cat filename

# View file page by page (press Space for next page)
more filename

# View file with navigation (install first with: apt install less)
less filename
# Use arrow keys to navigate, 'q' to quit

# View first 5 lines of file
head -n 5 filename
# The -n flag specifies number of lines to display from the beginning

# View last 5 lines of file
tail -n 5 filename
# The -n flag specifies number of lines to display from the end
# Useful for checking log file endings
```

#### Output Redirection and Pipes

**Basic Redirection:**
```bash
# Print text to terminal
echo hello

# Redirect output to file (overwrites existing content)
echo hello > hello.txt

# Copy content from one file to another
cat file1.txt > file2.txt

# Combine multiple files into one
cat file1.txt file2.txt > combined.txt

# Redirect command output to file
ls -l > file.txt
```

**Understanding Redirection Operators:**
- `>` (Output redirection): Sends output to a file, **overwrites** existing content
- `<` (Input redirection): Takes input from a file instead of keyboard

```bash
# Example with input redirection
sort < unsorted.txt

# Example with output redirection
ls -la > directory-listing.txt
```

#### Navigating Directories

```bash
# Move up one directory level (parent directory)
cd ..

# Move to specific path from current location (relative path)
cd ./subdirectory

# Absolute path (from root)
cd /home/user/documents

# Go to home directory
cd ~

# Go to previous directory
cd -
```

**Path Types:**
- `..` - Parent directory (one level up)
- `.` - Current directory
- `~` - Home directory
- `/` - Root directory (absolute path start)

## Docker Commands Cheatsheet

| Command | Description |
|---------|-------------|
| `docker pull <image>` | Download image from registry |
| `docker build -t <name> .` | Build image from Dockerfile |
| `docker run <image>` | Create and start container |
| `docker run -it <image>` | Run interactively with terminal |
| `docker run -d <image>` | Run in detached mode (background) |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers |
| `docker stop <container>` | Stop running container |
| `docker start <container>` | Start stopped container |
| `docker rm <container>` | Remove container |
| `docker rmi <image>` | Remove image |
| `docker exec -it <container> bash` | Execute bash in running container |
| `docker logs <container>` | View container logs |
| `docker images` | List all images |

## Useful Docker Flags

- `-it`: Interactive terminal
- `-d`: Detached mode (run in background)
- `-p`: Port mapping (e.g., `-p 8080:80`)
- `-v`: Volume mounting (e.g., `-v /host:/container`)
- `--name`: Assign name to container
- `--rm`: Automatically remove container when it stops
- `-e`: Set environment variables

## Resources

- [Docker Official Documentation](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Docker Getting Started Guide](https://docs.docker.com/get-started/)
- [Play with Docker](https://labs.play-with-docker.com/)

## Takeaway

> Docker revolutionizes application deployment by providing consistency across different environments. The ability to package an application with all its dependencies eliminates compatibility issues and streamlines the development-to-production pipeline.

---

**Learning Progress**: ✅ Basics Complete | 🔄 Intermediate In Progress

*Last Updated: October 2025*