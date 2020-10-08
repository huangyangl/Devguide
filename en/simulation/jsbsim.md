# JSBSim Simulation

[JSBSim](http://jsbsim.sourceforge.net/index.html) is a open source flight dynamics model (FDM) that supports many operating systems, including Microsoft Windows, Apple Macintosh, Linux, IRIX, Cygwin (Unix on Windows), etc.
JSBSim is the simulation 

Features include a fully configurable aerodynamics, propulsion system that can model complex flight dynamics of an aircraft. Also rotational earth effects are modeled into the dynamics. 


**Supported Vehicles:** Plane, Quadrotor, Hexarotor

{% youtube %}https://www.youtube.com/watch?v=iqdcN5Gj4wI{% endyoutube %}


> **Note** See [Simulation](/simulation/README.md) for general information about simulators, the simulation environment, and simulation configuration (e.g. supported vehicles).


## Installation (Ubuntu Linux) {#installation}

> **Note** These instructions were tested on Ubuntu 18.04

1. Install the usual [Development Environment on Ubuntu LTS / Debian Linux](../setup/dev_env_linux_ubuntu.md).
1. Install FlightGear:
   ```sh
   sudo add-apt-repository ppa:saiarcot895/flightgear
   sudo apt update
   sudo apt install flightgear
   ```
   This installs the latest stable FlightGear version from the PAA repository along with the the FGdata package.
   
   > **Tip** For some models (e.g. those with electric engines) the daily build with the newest features may be necessary.
     Install this using the [daily build PPA](https://launchpad.net/~saiarcot895/+archive/ubuntu/flightgear-edge).

1. Check that you are able to run FlightGear:
   ```
   fgfs --launcher
   ```
1. Set write permissions to the **Protocols** folder in the FlightGear installation directory:
   ```
   sudo chmod a+w /usr/share/games/flightgear/Protocols
   ```
   Setting the permissions is required because the PX4-FlightGear-Bridge puts the communication definition file here. 

Additional installation instructions can be found on [FlightGear wiki](http://wiki.flightgear.org/Howto:Install_Flightgear_from_a_PPA).   


## Running the Simulation {#running}

Run a simulation by starting PX4 SITL, specifying the airframe configuration of your choice.

The easiest way to do this is to open a terminal in the root directory of the PX4 *Firmware* repository and call `make` for the desired target.
For example, to start a plane simulation :
```sh
cd /path/to/Firmware
make px4_sitl_nolockstep flightgear_rascal
```

The supported vehicles and `make` commands are listed below (click on the links to see the vehicle images).

Vehicle | Command
--- | ---
[Standard Plane](../simulation/flightgear_vehicles.md#standard_plane) | `make px4_sitl_nolockstep flightgear_rascal`
[Ackerman vehicle (UGV/Rover)](../simulation/flightgear_vehicles.md#ugv) | `make px4_sitl_nolockstep flightgear_tf-r1`
[Autogyro](../simulation/flightgear_vehicles.md#autogyro) | `make px4_sitl_nolockstep flightgear_tf-g1`

The commands above launch a single vehicle with the full UI.
*QGroundControl* should be able to automatically connect to the simulated vehicle.

> **Note** For the full list of FlightGear build targets (highlighted) run:
  ```
  make px4_sitl_nolockstep list_vmd_make_targets | grep flightgear_
  ```
  For additional information see: [FlightGear Vehicles](../simulation/flightgear_vehicles.md) (this includes information about "unsupported" vehicles, and adding new vehicles).

<span></span>
> **Note** The [Installing Files and Code](../setup/dev_env.md) guide is a useful reference if there are build errors.


## Trouble Shooting



## Further Information

* [px4-jsbsim-bridge readme](https://github.com/Auterion/px4-jsbsim-bridge)
