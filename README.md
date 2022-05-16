
## Installation
This program is useful for ploting 2D representations of catmaid neurons, and reproducing these plots.

This program can be directly installed from github. (green code button, top right)
### conda environment
first make sure conda is installed. If you do not have conda, refer to online resources on how to install conda.

Once installed, we can make a conda environment.

```bash=
conda create --name pymaid
#activate
conda activate pymaid
```

Create a directory for pymaid.
```bash=
mkdir pymaid
cd pymaid
```

### Python version
The python version for running this script is python=3.6
```bash=
conda install python=3.6
```

### Dependencies
The script runs with pip\==21.3.1 and python-catmaid==2.0.4

If not already these versions, update your dependency, as such. 

```bash=
pip3 install --upgrade pip==21.3.1 wheel==0.37.1 setuptools==59.6.0

pip3 install python-catmaid==2.0.4 -U
```

### make environmental variables

The environmental variables are the login credentials required to access catmaid online. Which include, the catmaid server, and your API token which replaces your username and password to the server. Your API token can be got following the instructions at this website:
https://catmaid.readthedocs.io/en/stable/api.html#api-token

There are two ways to access catmaid online. The deemed safer version will be covered here, for the other option refere to this link:
https://pymaid.readthedocs.io/en/latest/source/intro.html

Add new environmental variables via the bash_profile file.

```bash=
nano ~/.bash_profile
```
When in nano, add the following lines to your code, with  respect to your account. 
```bash=
#instructions state CATMAID_SERVER_URL, but incorrect
export CATMAID_SERVER='https://www.your.catmaid-server.org'
export CATMAID_API_TOKEN='your_token'
```
Don't forget to source.
```bash=
source ~/.bash_profile
```

The script should be all ready to run.

## Usage
### input
The code can be run as follows
```bash=
python plot_pymaid.py [-h] [-v] -i PROJECT_ID
                      (-j JSON | -n NEURON [NEURON ...]) [-a]
                      [-V VOLUME [VOLUME ...]] [-c COLOUR [COLOUR ...]]
                      [-C VOLUME_COLOUR [VOLUME_COLOUR ...]]
                      [-p PERSPECTIVE PERSPECTIVE PERSPECTIVE] [-o OUTPUT]
```
The help page can be accessed with the -h or --help flag
```bash=
python plot_pymaid.py -h
python plot_pymaid.py --help
```
The program version can be accessed with the -v or --version flag
```bash=
python plot_pymaid.py -v
python plot_pymaid.py --version
```
There is two required arguments for running this program, PROJECT_ID and JSON or PROJECT_ID and NEURON. PROJECT_ID specifies which species stack you are looking for neurons in. JSON is a json file with neurons of interest and NEURON are neurons of interest directly typed out to the terminal.
```bash=
python plot_pymaid.py -i PROJECT_ID -j JSON
python plot_pymaid.py -i PROJECT_ID -n NEURON
```
The rest of the arguments are optional.

ANNOTATION, when annotations are how you are looking for neurons as opposed to by name.
```bash=
python plot_pymaid.py -i PROJECT_ID (-j JSON | -n NEURON) 
                      -a
```

Volume, for when you want to depict volumes in your plot.
```bash=
python plot_pymaid.py -i PROJECT_ID -j JSON -V VOLUME
python plot_pymaid.py -i PROJECT_ID -n NEURON -V VOLUME
```
COLOUR and VOLUME_COLOUR for when you want to have a specific colour for the neurons and the volumes respectively.
```bash=
python plot_pymaid.py -i PROJECT_ID -j JSON -c COLOUR
python plot_pymaid.py -i PROJECT_ID -n NEURON -c COLOUR

python plot_pymaid.py -i PROJECT_ID -j JSON -V VOLUME
                      -C VOLUME_COLOUR
python plot_pymaid.py -i PROJECT_ID -n NEURON -V VOLUME
                      -C VOLUME_COLOUR
```                      
PERSPECTIVE, for when you want a specific view of the neurons in your plot.
```bash=
python plot_pymaid.py -i PROJECT_ID (-j JSON | -n NEURON) 
                      -p PERSPECTIVE
```
Finally, OUTPUT, a output plot will be created with the specificied file name.
```bash=
python plot_pymaid.py -i PROJECT_ID (-j JSON | -n NEURON)
                      -o OUTPUT
```

### example inputs


for the perfect view
```bash=
python3 plot_pymaid.py -i 11 -n EPG PEN -a -V EB PB -p 7 300 310 -C 0,1,0,.2 0,1,0,.2
```

show you can search for 1 or more neurons, 1 or more volumes

### example output