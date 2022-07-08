# Workstation Tips and Tricks


## Installing Support Packages, libraries, etc..

I prefer installing packages/software from a repo, even better if they are "standard" repos.

### R and Rstudio
You can find both R and Rstudio in the Fedora repos
```
sudo dnf -y install R rstudio-desktop.x86_64
```

You may wish to install from the vendor directly
https://www.rstudio.com/products/rstudio/download/#download
```
 sudo dnf -y install https://download1.rstudio.org/desktop/rhel8/x86_64/rstudio-2022.07.0-548-x86_64.rpm
