# Problem 1
# Investigating the Range as a Function of the Angle of Projection  

## 1. Introduction  

Projectile motion is one of the fundamental concepts in classical mechanics, offering a rich framework to study motion under the influence of gravity. Despite its apparent simplicity, the mathematical description of projectile motion reveals intricate relationships between physical parameters such as initial velocity, gravitational acceleration, and the angle of projection.  

This report explores how the horizontal range of a projectile depends on its angle of projection. The study of projectile motion is widely applicable in fields ranging from sports science to ballistics, space exploration, and engineering. By analyzing the governing equations and simulating projectile trajectories, we aim to develop a deeper understanding of how initial conditions influence motion and the range of a projectile.  

## 2. Theoretical Foundation  

### 2.1 Equations of Motion  

Projectile motion is governed by Newton's second law, which leads to the following kinematic equations:  

$$x = v_0 \cos(\theta) t$$

$$y = v_0 \sin(\theta) t - \frac{1}{2} g t^2$$

where:  
- $x$ and $y$ are the horizontal and vertical coordinates of the projectile at time $t$,  
- $v_0$ is the initial velocity,  
- $\theta$ is the launch angle,  
- $g$ is the acceleration due to gravity (typically $ 9.81 \, m/s^2$ on Earth), and  
- $t$ is the time elapsed since launch.  

### 2.2 Time of Flight  

The time of flight can be derived by solving for when the projectile reaches the ground again $(y = 0)$:  

$$t_f = \frac{2 v_0 \sin(\theta)}{g}$$

### 2.3 Range of the Projectile  

The horizontal range $R$ is the horizontal distance traveled by the projectile before it lands, given by:  

$$R = v_0 \cos(\theta)t_f$$

Substituting $t_f$:  

$$R = \frac{v_0^2 \sin(2\theta)}{g}$$

This equation shows that the range depends on the square of the initial velocity, the gravitational acceleration, and the sine of twice the launch angle. The maximum range occurs when $\theta = 45^\circ$, as $\sin(90^\circ) = 1$ achieves the highest possible value.

### 2.4 Influence of Initial Conditions  

- **Initial Velocity**: Increasing $v_0$ increases the range quadratically.  
- **Gravity**: A higher gravitational acceleration decreases the range, as seen on planets with stronger gravity than Earth.  
- **Launch Angle**: The range follows a symmetric pattern about $45^\circ$, with identical ranges for complementary angles $ \theta$ and $90^\circ - \theta$.  

## 3. Analysis of the Range  

### 3.1 Range as a Function of the Angle of Projection  

Plotting $R$ versus $\theta$ reveals a parabolic shape, peaking at $45^\circ$. This reflects the competing influences of vertical and horizontal motion:  

- At low angles, horizontal velocity is high, but vertical motion is limited, reducing the time of flight.  
- At high angles, the projectile spends more time in the air but lacks sufficient horizontal velocity.  

### 3.2 Effect of Initial Velocity  

For different values of $v_0$, the range increases, but the peak always occurs at $45^\circ$. The effect of increasing $v_0$ is to stretch the range curve upwards.  

### 3.3 Effect of Gravitational Acceleration  

On the Moon, where $g \approx 1.62 \, m/s^2$, projectiles travel farther than on Earth for the same $v_0$. Conversely, on Jupiter $(g \approx 24.79 \, m/s^2)$, the range is significantly reduced.  

## 4. Practical Applications  

### 4.1 Sports Science  

In sports like soccer and basketball, understanding the optimal angle of launch is crucial for accurate shots. Players intuitively adjust the launch angle to maximize range or height.  

### 4.2 Ballistics  

The principles of projectile motion are applied in ballistics, where range calculations inform targeting accuracy. Real-world deviations from the ideal model arise due to air resistance, wind, and spin.  

### 4.3 Space Exploration  

Rocket launches follow a similar principle but account for varying gravitational forces and atmospheric drag. Understanding projectile motion is fundamental to orbital mechanics and mission planning.  

## 5. Implementation and Simulation  

To visualize the dependence of range on projection angle, we develop a Python script that simulates projectile motion and plots the range function.  

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
g = 9.81  # gravitational acceleration (m/s^2)
v0 = 20  # initial velocity (m/s)
angles = np.linspace(0, 90, 100)  # range of angles in degrees

# Compute range for each angle
ranges = (v0**2 * np.sin(2 * np.radians(angles))) / g

# Plot results
plt.figure(figsize=(8, 6))
plt.plot(angles, ranges, label=f'v0 = {v0} m/s', color='b')
plt.xlabel('Angle of Projection (degrees)')
plt.ylabel('Range (m)')
plt.title('Projectile Range as a Function of Angle')
plt.legend()
plt.grid()
plt.show()
```
[Colab](https://colab.research.google.com/drive/1hoZNFeee6syi7Yc08jQ9eyxHDQqNKHz7?authuser=1#scrollTo=MhV99wEBVqMB)

https://github.com/mirsaddoyan/solutions_repo/blob/main/docs/1%20Physics/1%20Mechanics/Unknown-8.png?raw=true


This script:  
- Computes the range for angles from $0^\circ$ to $90^\circ$.  
- Uses trigonometric functions to evaluate the theoretical equation.  
- Generates a graph displaying the relationship between range and angle.  

## 6. Limitations and Extensions  

### 6.1 Idealized Model Assumptions  

- **No Air Resistance**: Real-world projectiles experience drag, reducing their range.  
- **Flat Terrain**: Uneven surfaces alter the landing position.  
- **Constant Gravity**: At large distances, $g$ varies with altitude.  

### 6.2 Incorporating Air Resistance  

A more realistic model involves solving equations that account for drag forces:  

$F_d = \frac{1}{2} C_d \rho A v^2$

where $C_d$ is the drag coefficient, $\rho$ is air density, and $A$ is the cross-sectional area. Numerical methods such as Runge-Kutta can be employed to solve the resulting differential equations.  

## 7. Conclusion  

This report explored how the horizontal range of a projectile depends on its launch angle, highlighting key theoretical insights and computational modeling techniques. The parabolic dependence of range on angle, with a maximum at $45^\circ$, reflects a balance between horizontal and vertical motion. The study of projectile motion extends into many real-world domains, from sports to engineering and spaceflight.  

Future work could incorporate air resistance, spin effects, and varying gravitational fields to refine the model further. Understanding projectile motion remains a fundamental yet rich topic in physics and applied sciences.
