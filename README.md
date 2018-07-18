# Mavros_Drone

---

## Install Mavlink, Mavros
     
     
- Souce Inatallation    
  
```        
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws
catkin init
wstool init src
sudo apt-get install python-catkin-tools python-rosinstall-generator -y
wstool init ~/catkin_ws/src
# We use the Kinetic reference for all ROS distros as it's not distro-specific and up to date
rosinstall_generator --rosdistro kinetic mavlink | tee /tmp/mavros.rosinstall
rosinstall_generator --upstream mavros | tee -a /tmp/mavros.rosinstall
wstool merge -t src /tmp/mavros.rosinstall
wstool update -t src -j4
rosdep install --from-paths src --ignore-src -y
./src/mavros/mavros/scripts/install_geographiclib_datasets.sh
catkin build
#Needed or rosrun can't find nodes from this workspace.
source devel/setup.bash
```
     
     
## Install Px4
