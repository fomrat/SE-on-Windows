## Windows 10 users (build 1709 / cmd ver 10.0.16299.309)

#update the installation -- 15.6 MB
sudo apt-get update

# Clone the tools repo
git clone https://github.com/standardebooks/tools.git

# Install some pre-flight dependencies
# lxml requires the following packages for its pip build process: python3-dev libxml2-dev libxslt1-dev zlib1g-dev
sudo apt install -y python3-pip python3-dev libxml2-dev libxslt1-dev zlib1g-dev libxml2-utils librsvg2-bin libimage-exiftool-perl imagemagick epubcheck default-jre inkscape calibre curl git

# Install required fonts
mkdir -p ~/.fonts/
curl -s -o ~/.fonts/LeagueSpartan-Bold.otf "https://raw.githubusercontent.com/theleagueof/league-spartan/master/LeagueSpartan-Bold.otf"
curl -s -o ~/.fonts/OFLGoudyStM.otf "https://raw.githubusercontent.com/theleagueof/sorts-mill-goudy/master/OFLGoudyStM.otf"
curl -s -o ~/.fonts/OFLGoudyStM-Italic.otf "https://raw.githubusercontent.com/theleagueof/sorts-mill-goudy/master/OFLGoudyStM-Italic.otf"

# Refresh the local font cache
sudo fc-cache -fv

# Install python-dev and dependencies -- Win10 build doesn't have these, so we can't do requirements.txt yet. Definitely.
sudo apt-get install build-essential libssl-dev libffi-dev python-dev
    
# Install python dependencies
pip3 install -r ./tools/requirements.txt

# Install hyphenation dictionaries for the pyhyphen library
python3 -c "exec(\"from hyphen import dictools\\ndictools.install('en_GB')\\ndictools.install('en_US')\")"

# Install python pip and git -- the SE build will fail without these
sudo apt install python-pip
sudo -H pip install gitpython
    
```
