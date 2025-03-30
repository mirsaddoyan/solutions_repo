# Problem 2
# **Escape Velocities and Cosmic Velocities**  

## **1. Introduction**  

The ability of an object to leave the gravitational influence of a celestial body is a fundamental concept in space exploration. Understanding how fast a spacecraft or any object must travel to achieve a stable orbit, escape a planet, or even leave a star system entirely is crucial for designing space missions, launching satellites, and interplanetary travel.  

The **escape velocity** is the minimum speed an object must have to completely overcome a planet’s gravitational pull without further propulsion. More generally, the **cosmic velocities** define different velocity thresholds required for various stages of motion in space:  
1. The **first cosmic velocity** (orbital velocity) allows an object to maintain a stable circular orbit around a planet.  
2. The **second cosmic velocity** (escape velocity) is the minimum velocity needed to leave the planet’s gravitational influence.  
3. The **third cosmic velocity** (interplanetary velocity) is the speed required to escape a star’s gravitational field from a planet’s orbit.  

This report aims to:  
1. Define and derive the equations for the first, second, and third cosmic velocities.  
2. Analyze the factors affecting these velocities, such as planetary mass and radius.  
3. Compute and visualize these velocities for different celestial bodies, including Earth, Mars, and Jupiter.  
4. Explore their significance in space exploration, including satellite deployment, deep-space missions, and potential interstellar travel.  

---

## **2. Theoretical Foundation**  

### **2.1 The First Cosmic Velocity (Orbital Velocity)**  

The **first cosmic velocity** ($v_1$) is the speed required to maintain a stable circular orbit around a planet without falling back to its surface. This is also known as the **orbital velocity** and is derived by equating the **gravitational force** to the required **centripetal force** for circular motion.  

The gravitational force acting on an object of mass $m$ orbiting a planet of mass $M$ at radius $r$ is:  

$$F_g = \frac{G M m}{r^2}$$

The required centripetal force to maintain circular motion is:  

$$F_c = \frac{m v_1^2}{r}$$

Setting these equal to each other:  

$$\frac{G M m}{r^2} = \frac{m v_1^2}{r}$$

Canceling $m$ and solving for $v_1$:  

$$v_1 = \sqrt{\frac{G M}{r}}$$

This is the velocity needed for a circular orbit at radius $r$. If an object moves slower than this, it will fall back to the planet; if it moves faster, it will enter an elliptical or escape trajectory.  

---

### **2.2 The Second Cosmic Velocity (Escape Velocity)**  

The **second cosmic velocity** ($v_2$) is the **escape velocity**, which is the minimum speed an object must reach to break free from a planet’s gravitational field without additional propulsion.  

We derive this by considering **energy conservation**. A body is considered to have escaped if its **total mechanical energy** is non-negative:  

$$E = K + U \geq 0$$

where:  
- $K = \frac{1}{2} m v^2$ is the **kinetic energy**,  
- $U = -\frac{G M m}{r}$ is the **gravitational potential energy**.  

At the planet’s surface ($r = R$), the object must have enough kinetic energy to reach $r \to \infty$, where $U \to 0$. Thus, we set:  

$$\frac{1}{2} m v_2^2 - \frac{G M m}{R} = 0$$

Solving for $v_2$:  

$$v_2 = \sqrt{\frac{2 G M}{R}}$$

This means that to completely escape the gravitational pull of a planet, an object must travel at least $v_2$. If launched with a velocity lower than $v_2$, it will eventually fall back or enter an elliptical orbit.  

---

### **2.3 The Third Cosmic Velocity (Interplanetary Velocity)**  

The **third cosmic velocity** ($v_3$) is the velocity required for an object to escape from a **star’s gravitational field** while starting from a planet’s orbit. This applies to interstellar missions, where spacecraft need to leave the Solar System entirely.  

We can derive $v_3$ similarly to $v_2$, but now considering escape from the **Sun’s gravitational field** rather than a planet’s. If an object starts from a planet at distance $R_p$ from the Sun (e.g., Earth’s orbital radius $R_E$), the escape velocity from the Sun is:  

$$v_3 = \sqrt{v_2^2 + v_{\text{orb}}^2}$$

where:  
- $v_2 = \sqrt{\frac{2 G M_{\odot}}{R_p}}$ is the **escape velocity from the Sun** at distance $R_p$,  
- $v_{\text{orb}} = \sqrt{\frac{G M_{\odot}}{R_p}}$ is the **orbital velocity of the planet** around the Sun.  

Simplifying:  

$$v_3 = \sqrt{3 \frac{G M_{\odot}}{R_p}}$$

This shows that interstellar probes must exceed **three times the Sun’s orbital velocity** at that location to escape its gravity completely.  

---

## **3. Computational Analysis**  

To visualize these velocities, we compute and compare them for **Earth, Mars, and Jupiter**.  

### **3.1 Python Simulation of Escape and Cosmic Velocities**  

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.674e-11  # Gravitational constant (m^3 kg^-1 s^-2)

# Celestial bodies (mass in kg, radius in meters)
bodies = {
    "Earth": {"M": 5.97e24, "R": 6.371e6},
    "Mars": {"M": 6.39e23, "R": 3.389e6},
    "Jupiter": {"M": 1.90e27, "R": 6.9911e7}
}

# Calculate velocities
for planet, data in bodies.items():
    M, R = data["M"], data["R"]
    v1 = np.sqrt(G * M / R)  # First cosmic velocity
    v2 = np.sqrt(2 * G * M / R)  # Second cosmic velocity
    print(f"{planet}:")
    print(f"  First Cosmic Velocity (Orbital) = {v1:.2f} m/s")
    print(f"  Second Cosmic Velocity (Escape) = {v2:.2f} m/s\n")

# Plot escape velocity vs. planetary radius
radii = np.array([data["R"] for data in bodies.values()])
velocities = np.array([np.sqrt(2 * G * data["M"] / data["R"]) for data in bodies.values()])

plt.figure(figsize=(8, 6))
plt.scatter(radii / 1e6, velocities / 1e3, color='r', label='Escape Velocity')
plt.xlabel("Planetary Radius (x10^6 m)")
plt.ylabel("Escape Velocity (km/s)")
plt.title("Escape Velocities for Different Planets")
plt.legend()
plt.grid()
plt.show()
```
[Colab](https://colab.research.google.com/drive/1IqRR9KKWCAXNI3wQw8ww3D9J9YYc_tqs?authuser=1)

![Example Image](https://github.com/mirsaddoyan/solutions_repo/blob/main/docs/1%20Physics/2%20Gravity/Unknown-11.png?raw=true)

### **3.2 Interpretation of Results**  

- **Earth:**  
  - Orbital velocity: ~7.91 km/s  
  - Escape velocity: ~11.19 km/s  

- **Mars:**  
  - Orbital velocity: ~3.58 km/s  
  - Escape velocity: ~5.02 km/s  

- **Jupiter:**  
  - Orbital velocity: ~42.1 km/s  
  - Escape velocity: ~59.5 km/s  

Since Jupiter has a much larger mass than Earth or Mars, its escape velocity is significantly higher, requiring much more energy for missions to leave its gravitational influence.  

---

## **4. Conclusion**  

Escape and cosmic velocities are crucial concepts in space travel. The relationships derived help determine the speeds needed to reach orbit, escape planets, and even leave the Solar System. Understanding these velocities allows scientists and engineers to design efficient space missions, optimize fuel consumption, and explore beyond Earth.
