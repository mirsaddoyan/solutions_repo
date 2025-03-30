# Problem 3
# Escape Velocities and Cosmic Velocities

## Motivation:
The concept of **escape velocity** is crucial for understanding the conditions required to leave a celestial body's gravitational influence. Extending this concept, the **first, second, and third cosmic velocities** define the thresholds for orbiting, escaping, and leaving a star system. These principles underpin modern space exploration, from launching satellites to interplanetary missions.

---

## Task Breakdown

### 1. Defining the First, Second, and Third Cosmic Velocities

#### **Escape Velocity (Second Cosmic Velocity)**

Escape velocity is the minimum velocity an object must have to escape the gravitational pull of a celestial body without further propulsion. It is defined as the velocity at which the **kinetic energy** of the object equals the **gravitational potential energy**.

Mathematically, escape velocity $v_e$ is given by:

$[
v_e = \sqrt{\frac{2GM}{R}}
]$

Where:
- $G$ is the gravitational constant,
- $M$ is the mass of the celestial body,
- $R$ is the distance from the center of the celestial body to the object.

Escape velocity is critical for space exploration because it determines the energy required to launch a spacecraft or satellite into space.

#### **First Cosmic Velocity (Orbital Velocity)**

The first cosmic velocity is the velocity an object must have to enter into a stable orbit around a celestial body. This is the velocity at which the **centripetal force** required to maintain an orbit equals the gravitational force acting on the object.

The orbital velocity $v_o$ is given by:

$[
v_o = \sqrt{\frac{GM}{R}}
]$

Where:
- $G$ is the gravitational constant,
- $M$ is the mass of the celestial body,
- $R$ is the distance from the center of the celestial body to the orbiting object.

The first cosmic velocity is vital for placing satellites into orbit, as it ensures the object moves fast enough to balance gravitational forces.

#### **Third Cosmic Velocity (Escape from the Solar System)**

The third cosmic velocity is the velocity an object needs to escape the gravitational influence of the Sun (or any star) and move away from the star system indefinitely. This velocity is calculated using the gravitational force of the Sun and takes into account the distance from the object to the Sun.

The third cosmic velocity $v_3$ is given by:

$[
v_3 = \sqrt{\frac{2GM_{\text{sun}}}{R_{\text{sun}}} + \frac{v_{\text{escape}}^2}{2}}
]$

Where:
- $M_{\text{sun}}$ is the mass of the Sun,
- $R_{\text{sun}}$ is the distance from the Sun to the object,
- $v_{\text{escape}}$ is the escape velocity at the Earth's surface or any other celestial body in question.

This velocity is essential for interstellar travel or missions that aim to leave the solar system.

---

### 2. Mathematical Derivations and Parameters Affecting These Velocities

The escape velocities and cosmic velocities depend on the mass $M$ of the celestial body and the distance $R$ from the center of mass to the object. Higher mass and smaller radii lead to higher velocities, meaning it requires more energy to escape from more massive bodies or closer objects.

The **gravitational constant** $G$ remains a constant across calculations, but the mass of the object and the distances to the object play critical roles in calculating these velocities. Therefore, for different planets or celestial bodies, the velocities vary significantly.

---

### 3. Calculating and Visualizing These Velocities for Different Celestial Bodies

We can calculate the first, second, and third cosmic velocities for various celestial bodies, such as **Earth**, **Mars**, and **Jupiter**, using the formulas above.

#### **Python Code for Cosmic Velocities**

Below is the Python code to calculate and visualize the escape velocities and cosmic velocities for Earth, Mars, and Jupiter:

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # Gravitational constant in m^3 kg^-1 s^-2

# Masses and radii of celestial bodies (in SI units)
celestial_bodies = {
    'Earth': {'M': 5.972e24, 'R': 6.371e6},
    'Mars': {'M': 6.4171e23, 'R': 3.3962e6},
    'Jupiter': {'M': 1.8982e27, 'R': 6.991e7},
}

# Function to calculate the first and second cosmic velocities
def cosmic_velocities(M, R):
    v1 = np.sqrt(G * M / R)  # First cosmic velocity (orbital velocity)
    v2 = np.sqrt(2 * G * M / R)  # Second cosmic velocity (escape velocity)
    return v1, v2

# Calculate velocities for each celestial body
velocities = {}
for body, values in celestial_bodies.items():
    v1, v2 = cosmic_velocities(values['M'], values['R'])
    velocities[body] = {'v1': v1, 'v2': v2}

# Plotting the velocities
labels = list(celestial_bodies.keys())
v1_values = [velocities[body]['v1'] for body in labels]
v2_values = [velocities[body]['v2'] for body in labels]

x = np.arange(len(labels))

fig, ax = plt.subplots(figsize=(10, 6))

bar_width = 0.35
ax.bar(x - bar_width/2, v1_values, bar_width, label='First Cosmic Velocity (Orbital)', color='b')
ax.bar(x + bar_width/2, v2_values, bar_width, label='Second Cosmic Velocity (Escape)', color='r')

ax.set_xlabel('Celestial Bodies')
ax.set_ylabel('Velocity (m/s)')
ax.set_title('First and Second Cosmic Velocities for Different Celestial Bodies')
ax.set_xticks(x)
ax.set_xticklabels(labels)
ax.legend()

plt.tight_layout()
plt.show()
```
[Colab](https://colab.research.google.com/drive/1YeT0Dqua7RCqWjgrzE43nqNaLbTKGAXo?authuser=1)

![Example Image](https://github.com/mirsaddoyan/solutions_repo/blob/main/docs/1%20Physics/2%20Gravity/Unknown-12.png?raw=true)

---
### 4. Importance in Space Exploration

#### **Launching Satellites and Spacecrafts**
Understanding escape and orbital velocities is critical for launching satellites. The **first cosmic velocity** ensures that satellites remain in stable orbits around Earth, allowing them to maintain a consistent path without falling back to the planet's surface. The **second cosmic velocity** is necessary for launching spacecraft that need to escape Earth's gravitational influence and travel into space.

For instance, when sending satellites to low Earth orbit (LEO), they must reach the first cosmic velocity, which ensures they remain in orbit. For missions that aim to go beyond Earth's orbit, such as interplanetary missions to Mars or beyond, the second cosmic velocity is required to escape Earth's gravity.

#### **Missions to Other Planets**
For interplanetary missions, spacecraft must reach **escape velocity** to leave Earth's gravity well and then navigate towards other planets. After escaping Earth's gravitational field, spacecraft will use the gravitational forces of other planets to adjust their trajectory or speed (via gravity assists). 

For example, the **Mars Rover missions** require spacecraft to escape Earth's gravity (second cosmic velocity) to head towards Mars. Similarly, for probes like Voyager, the **third cosmic velocity** is needed to leave the solar system entirely.

#### **Interstellar Travel**
The **third cosmic velocity** represents the velocity required for interstellar travel, allowing spacecraft to break free from the Sun's gravity and travel to other star systems. While current technology does not allow us to achieve this velocity, understanding it is fundamental for future space exploration.

This velocity, calculated for a spacecraft at the Earth's surface, is approximately 16.7 km/s, significantly higher than the velocities needed for orbital or escape purposes. While still beyond current technology, efforts like **breakthrough propulsion** (e.g., light sails or ion drives) are being researched to achieve the high speeds required for interstellar missions.

---

### 5. Graphical Representations

The following bar graph visualizes the **first and second cosmic velocities** for **Earth**, **Mars**, and **Jupiter**. This representation allows us to understand how these velocities vary across different celestial bodies:

- **Jupiter** has the highest escape and orbital velocities due to its larger mass and size compared to Earth and Mars.
- **Mars** has the lowest velocities because of its smaller mass and radius in comparison to Earth and Jupiter.
- **Earth** provides an intermediate set of velocities, making it the baseline for most space missions.

#### **Graph Interpretation**
From the graph, we observe the following trends:
- The escape velocity (second cosmic velocity) is always greater than the orbital velocity (first cosmic velocity) for all bodies.
- Larger planets like Jupiter require higher velocities to escape their gravitational fields compared to smaller planets like Mars.


---


### Conclusion

The concept of **escape velocity** and the **first, second, and third cosmic velocities** is essential for understanding the physics of space exploration. By calculating and visualizing these velocities, we gain insights into the challenges of launching spacecraft, sending probes to distant planets, and contemplating future interstellar travel. These velocities determine the energy required to launch missions into orbit, escape planetary gravity, and venture beyond our Solar System.


---

### **Summary:**
- **Task 1:** Define and explain the first, second, and third cosmic velocities, with their respective mathematical formulations.
- **Task 2:** Discuss the factors that affect these velocities, such as mass and radius of celestial bodies.
- **Task 3:** Provide Python code to calculate and visualize the first and second cosmic velocities for Earth, Mars, and Jupiter.
- **Task 4:** Explain the importance of these velocities in space exploration, particularly for satellite launches, planetary missions, and interstellar travel.

