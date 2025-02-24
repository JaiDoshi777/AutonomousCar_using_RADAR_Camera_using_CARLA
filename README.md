# AutonomousCar_using_RADAR_using_CARLA


# Simulation Architecture
Implements a client-server model using CARLA's Python API (0.9.X+)

Utilizes CARLA's Traffic Manager for autonomous agent coordination with configurable safety margins (2m following distance)

Features dynamic spectator camera tracking with 3D spatial offsets relative to ego vehicle

# Sensor Configuration
RADAR Sensor:

30°×30° dual-axis field of view (FOV)

100m detection range with 15,000 points/sec resolution

Mounted at vehicle front (2m X-offset, 1m Z-offset)

Outputs 4D point cloud: velocity, azimuth (radians), altitude (radians), depth

# Data Pipeline
Raw Data Processing:

Converts byte-stream radar data to structured numpy arrays (float32)

Spherical-to-Cartesian coordinate transformation (azimuth/depth extraction)

Real-time coordinate system alignment (radian-to-degree conversion)

Visualization System:

Matplotlib-based dynamic scatter plot

Cartesian mapping: azimuth (-50° to +50°) vs depth (0-100m)

Asynchronous plot updates using interactive mode (plt.ion())

# Autonomy Stack
TM-controlled vehicle autonomy with deterministic seed (0)

Continuous world state synchronization via world.tick()

Camera tracking updates at 10Hz frequency (100ms intervals)

# Performance Considerations
Managed simulation timing with CPU load balancing (explicit sleep intervals)

Resource cleanup protocol for sensor/vehicle destruction

Robust exception handling for graceful shutdown (KeyboardInterrupt)

# Technical Dependencies
CARLA 0.9.X+ server instance (localhost:2000)

Python 3.7+ with numpy for array operations

Matplotlib for real-time visualization

This implementation demonstrates a closed-loop perception system for autonomous vehicles, integrating sensor physics, spatial transforms, and real-time data visualization within a photorealistic simulation environment.


# Video Demonstration

NOTE: Due to low system specs, the approach to take video is not standard


https://github.com/user-attachments/assets/556b961a-58df-4749-9b39-4248365f1f94


