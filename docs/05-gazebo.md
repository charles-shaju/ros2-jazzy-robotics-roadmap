# Gazebo Simulation

URDF + RViz2 completed

Since your robot model is now visible in RViz2 and its joints move using the sliders, the next topic is **Gazebo Simulation**.

Until now, we have visualized a robot. Next, we will make it interact with a simulated physical world.

## **1. What is Gazebo?**

[ROS 2 Jazzy Tutorial: Develop and Control Gazebo Model of Mobile Robot in ROS 2 and Python – Fusion of Engineering, Control, Coding, Machine Learning, and Science](https://images.openai.com/static-rsc-4/Rauw_KUbR_xa3C_SYNXTfKyuhHziOWNRlY1xzpnDFLWw6d3XvSshVEubnpb5Z5vv4fcxcd7tn18vseZ1OqKYHiuigxKbQJuBvPQNq6DjWLpPvz4AudhKhgbfmP4LI5Jlv_5IAlRHouIwEDHpGvZxTSd4fNUIu5dSJKVarVRwHWc?purpose=inline)

[Install Gazebo for ROS 2 in under a minute | Ubuntu](https://images.openai.com/static-rsc-4/LM5DlWoxJxoiNbaoOMG18wLv0tmm0aGmLbuEfx5ktdbmj-OAMEUfrgxtQIGNvG_6Ktzc5Y_1whqiXPVjCvMBvdwx0WQPAscB3fQGgZlvXwqoQNbfsR74iV0wqANoyAXQm3lZA_pt4ZmjsUca5iuWuyKXpeyQZFp8Sq7hYVqGnoo?purpose=inline)

[Additional Simulation Worlds — Dingo Tutorials 0.0.5 documentation](https://images.openai.com/static-rsc-4/bU70pUiOEnBnmkFhvzvUYMPYa55Zs3_UjXlrdCHsgZ--9ahbYo3JQj2lEOAbh3wZK60BWkCI5v8d_NFKdVEfODOibYL0RmvkiXg0LjyU3rx2R687dj-kHOexFjYORSMV-Ys7DBfEcuDpUECFMjb_fXkHRoHL1KWEsdjtYTYi1CU?purpose=inline)

9

Gazebo is a robotics simulator that provides:

- **Physics:** Gravity, friction, collisions and motion.
    
- **Sensors:** LiDAR, cameras, IMU and other simulated sensors.
    
- **Robot control:** Simulated motors and wheel movement.
    
- **Environment:** Floors, walls and obstacles.
    
- **ROS 2 integration:** Communication between Gazebo and ROS 2 nodes.
    

### **RViz2 vs Gazebo**

|RViz2|Gazebo|
|---|---|
|Visualization tool|Physics simulator|
|Displays robot model|Simulates robot movement|
|Displays TF and sensor data|Generates simulated sensor data|
|No physics simulation|Gravity and collision physics|
|Useful for debugging|Useful for testing robot behavior|

## **2. Our learning roadmap**

1. **Install Gazebo Harmonic** — compatible with ROS 2 Jazzy
    
2. **Understand Gazebo architecture** — worlds, models, plugins and simulation
    
3. **Spawn our URDF robot** into Gazebo
    
4. **Add collision and inertial properties** to our robot
    
5. **Implement differential-drive control** for two wheels
    
6. **Integrate `ros2_control`** and controllers
    
7. **Drive using teleop** and keyboard commands
    
8. **Connect Gazebo with RViz2** to visualize TF and sensor data
    

## **3. Practical 1 — Install Gazebo Harmonic**

We will run Gazebo on your **Ubuntu 24.04 laptop**, not your headless Raspberry Pi 4, because Gazebo's graphical interface is more suitable for the laptop.

Open a terminal on your laptop.

**Step 1 — Check ROS 2**

```
echo $ROS_DISTRO
```

Expected output:

```
jazzy
```

**Step 2 — Install Gazebo integration**

```
sudo apt update

sudo apt install ros-jazzy-ros-gz
```

This installs the ROS 2 integration packages for Gazebo, including tools for launching Gazebo and exchanging messages.

**Step 3 — Check Gazebo**

```
gz sim --version
```

You should see Gazebo Sim version information.

**Step 4 — Launch an empty world**

```
gz sim empty.sdf
```

[Use ROS 2 to interact with Gazebo — Gazebo harmonic documentation](https://images.openai.com/static-rsc-4/FbjUqfHpfwViVBQKfQ6YElXaZk6BzgjEAFlTAWO5HbXWU_4bJAD68lJjR6KZTbhJy7mTb9CQximl7fB4KmheZAxvtsRZgRVCsOJ68n-vPetQQuMvAyM4UVuSWT-4dtg607GgBhaROxiO2hrEWgFjGJkdYGr-3HfXkdTisCZ4AT4?purpose=inline)

[gazebosim.org](https://gazebosim.org/docs/harmonic/ros2_integration/)

A Gazebo window should open with an empty simulation environment.

## **4. Understand how ROS 2 communicates with Gazebo**

Bidirectional communication between ROS 2 and Gazebo through ros_gz_bridge

The `ros_gz_bridge` package allows messages to pass between ROS 2 topics and Gazebo Transport topics.

For example, ROS 2 can send velocity commands to a simulated robot, while Gazebo can provide odometry and sensor readings back to ROS 2.

## **Your task**

Run these commands on your laptop:

```
gz sim --version
gz sim empty.sdf
```

---

[Next: Spawn your robot in Gazebo](./06-gazebo-spawn.md)
