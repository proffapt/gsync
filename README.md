<div id="top"></div>

<!-- PROJECT SHIELDS -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]
  
  <h3 align="center">dcSAGC</h3>

  <p align="center">
    <i>Automate the unique process(by proffapt) for syncing your configuration from your local machine to github.</i>
    <br />
    <a href="https://github.com/proffapt/dcSAGC"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/proffapt/dcSAGC/issues">Report Bug</a>
    ·
    <a href="https://github.com/proffapt/dcSAGC/issues">Request Feature</a>
  </p>
</div>


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#why-linking-config-files-?">Why linking config files ?</a></li>
        <li><a href="#supports">Supports</a></li>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#changelog">Change.log</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>


<!-- ABOUT THE PROJECT -->
## About The Project

dcSAGC is a very useful tool for those who like to sync their configuration files in real-time to github, so how does it exactly do that? Read the code for detailed understanding.. but for an overview.. here's a short explaination:
* `create mode`:
1. It checks for config file you specified, if it doesn't exist it will create it.
2. Then it sets up the git folder locally and on github used to sync the config file, copies the earlier config file in here and creates a link to this config file in the original location, along with creating README.md file if it doesn't exist and syncs this folder to your remote repo you entered during the process. --> Configuration synced for first time.
3. Then creates a sync file in specified location, if that location is linked with some remote github repo it will sync it there too else will move ahead.
4. Now whenever you will use the specified alias, it will open your fav text editor, and after you finish editing, the sync script will sync the config file to the github repo every time you edit it..
* `delete mode`:
1. Reverses all the mess it made, putting back the config file where it was supposed to be, replacing the link, deleting the github folder.
* `default mode`:
1. Stores only the value for `-g` arg
2. Just stores the value in a file inside the script folder and then sources it, obviously with some not so simple if-else nested conditions for various cases.

<p align="right">(<a href="#top">back to top</a>)</p>

<div id="why-linking-config-files-?"></div>

### Why linking config files ?

- Suppose you wanna sync your .bashrc in `~/`, you will have to `git init` your `~/` which will show everywhere `(main)` in your terminal and might clash with your sub directories which are some local git projects, so yeah just move it somewhere else.. link that to original location and sync the file now

<p align="right">(<a href="#top">back to top</a>)</p>

<div id="supports"></div>

### Supports:
1. Shells
    * `bash`
    * `fish`
    * `zsh`
    * `sh`
    * `csh`
    * `ksh`
    * `tcsh`
2. OS(s)
    * MacOS[`BSD` based]
    * any *nix[`GNU+Linux` and `Unix`]

<p align="right">(<a href="#top">back to top</a>)</p>

### Built With

This project is made with following langs/frameworks.

* Bash


<p align="right">(<a href="#top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started

To get a local copy up and running follow these simple steps.

### Prerequisites
You will need to install the following dependencies for the project to work.
* `git`
* `gh`
  ```sh
  gh auth login
  gh auth refresh -h github.com -s delete_repo
  ```

<p align="right">(<a href="#top">back to top</a>)</p>

### Installation

_Now since we are done with the setting up of environment suitable for the project to compile/run, let's install and configure the project on your system locally now._
1. Clone the repo
   ```sh
   git clone https://github.com/proffapt/dcSAGC.git
   ```
2. Make the script executable
   ```sh
   cd ./dcSAGC
   chmod +x ./dcSAGC
   ```

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- USAGE EXAMPLES -->
## Usage

1. Execute the help menu for script
   ```sh
   ./dcSAGC -h
   ```
<div align="center">
  <a href="https://github.com/proffapt/dcSAGC">
    <img src=".images/ss_help.png" alt="product screenshot">
  </a>
</div>

2. Use cases for the script are as follows:
* Create mode
  ```sh
  dcSAGC create -s ~/sandbox/dcSAGC/sync_file/syncer -a test.e -g ~/sandbox/dcSAGC/git_folder/ -c ~/sandbox/dcSAGC/config_file/config.file
  ```

* Delete mode
  ```sh
  dcSAGC delete -s ~/sandbox/dcSAGC/sync_file/syncer -a test.e -g ~/sandbox/dcSAGC/git_folder/ -c ~/sandbox/dcSAGC/config_file/config.file
  ```
* Default mode
   ```sh
   dcSAGC default -g ~/sandbox/dcSAGC/github_folder/
   dcSAGC create -s ~/sandbox/dcSAGC/sync_file/syncer -a test.e -c ~/sandbox/dcSAGC/config_file/config.file
   dcSAGC delete -s ~/sandbox/dcSAGC/sync_file/syncer -a test.e -c ~/sandbox/dcSAGC/config_file/config.file
   ```

3. Source your configuration file!
4. Now if you used `create` mode, use the alias(`test.e` here) to edit your configuration file(`config.file` here), the sync script(`syncer` here)
will do it's job and sync the configuration file to specified github repo.
    ```sh
    test.e
    ```
  
#### * See output screenshots of various cases in [.images](https://github.com/proffapt/dcSAGC/tree/main/.images) folder.

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- ROADMAP -->
## Roadmap
- [x] Add the docs to repo
- [x] Add the logic for create mode
- [x] Add the logic for delete mode
- [x] Beautify help menu
- [x] Adding banner
- [x] Completing the Documentation
- [x] Add banner
- [x] Implement in script git repo creation
- [x] Creating more robust logic for git folder manipulation
- [x] Making the codebase much more readable
- [x] Add the logic for default mode
- [x] Add support for more shells `sh`, `csh`, `ksh` and `tcsh`
- [x] Cleaning code for the one last time

See the [open issues](https://github.com/proffapt/dcSAGC/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- Changelog -->
# Changelog

## v1.1.3

### Added or Changed
- Added freedom to use or not use '/' after github folder name
- Added in script git repo creation
- More robust logic for github folder manipulation
- More robust logic for alias management
- Added banner
- Much more organised and efficient code base
- Added default mode to save some default input args
- Adding support for more shells: `sh`, `csh`, `ksh` and `tcsh`

### Removed

- Useless multiple occurences of code.. implementing DRY principle
- `nvim` as dependency, now use your fav text editor
- Removing git storage command from prerequisites
- Many typos in the output of script
- `-m` argument, use the mode name directly

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- LICENSE -->
## License

Distributed under the BSD-2-Clause License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

Arpit Bhardwaj - [Twitter](https://twitter.com/proffapt) - [Telegram](https://t.me/proffapt) - proffapt@protonmail.com

Company website: [Cybernity](https://cybernity.org) - [CybernityForum](https://cybernity.group)

Project Link: [https://github.com/proffapt/dcSAGC](https://github.com/proffapt/dcSAGC)

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [Choose an Open Source License](https://choosealicense.com)
* [Img Shields](https://shields.io)
* [GH manual](https://cli.github.com/manual/gh_repo_create)
* [sed - BSD v/s GNU/Linux](https://unix.stackexchange.com/questions/401905/bsd-sed-vs-gnu-sed-and-i)
* [Detect changes in git folder](https://stackoverflow.com/questions/13715544/shell-script-to-check-git-for-changes-and-then-loop-through-changed-files)

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->

[contributors-shield]: https://img.shields.io/github/contributors/proffapt/dcSAGC.svg?style=for-the-badge
[contributors-url]: https://github.com/proffapt/dcSAGC/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/proffapt/dcSAGC.svg?style=for-the-badge
[forks-url]: https://github.com/proffapt/dcSAGC/network/members
[stars-shield]: https://img.shields.io/github/stars/proffapt/dcSAGC.svg?style=for-the-badge
[stars-url]: https://github.com/proffapt/dcSAGC/stargazers
[issues-shield]: https://img.shields.io/github/issues/proffapt/dcSAGC.svg?style=for-the-badge
[issues-url]: https://github.com/proffapt/dcSAGC/issues
[license-shield]: https://img.shields.io/github/license/proffapt/dcSAGC.svg?style=for-the-badge
[license-url]: https://github.com/proffapt/dcSAGC/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/proffapt
[product-screenshot]: .images/screenshot.png
