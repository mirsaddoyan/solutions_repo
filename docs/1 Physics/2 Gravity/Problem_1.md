# Problem 1
# **Orbital Period and Orbital Radius**  

## **1. Introduction**  

The motion of celestial bodies, from planets orbiting the Sun to artificial satellites around Earth, follows well-defined physical laws that have been studied for centuries. One of the most fundamental relationships in celestial mechanics is **Kepler’s Third Law**, which states that the square of a planet’s orbital period is proportional to the cube of its orbital radius.  

This relationship not only provides insights into the motion of planets and satellites but also plays a crucial role in calculating planetary masses, determining distances in the universe, and designing space missions. The elegance of Kepler’s Third Law lies in its simplicity and universality—it applies to any object in orbit around a massive body, as long as gravitational forces dominate.  

In this report, we:  
1. Derive Kepler’s Third Law from Newton’s laws of motion and universal gravitation.  
2. Explore its implications in astronomy, including its use in determining planetary masses and understanding exoplanetary systems.  
3. Analyze real-world examples, such as the Moon’s orbit around Earth and the orbits of planets in the Solar System.  
4. Develop a computational model to simulate circular orbits and verify the mathematical relationship.  
5. Discuss how this relationship extends to elliptical orbits and the broader field of celestial mechanics.  

By combining theoretical analysis with numerical simulations, we aim to deepen our understanding of orbital mechanics and its relevance to both historical and modern space exploration.  

---

## **2. Theoretical Foundation**  

### **2.1 Derivation of Kepler’s Third Law**  

To understand the relationship between orbital period and radius, we begin with Newton’s **Law of Universal Gravitation**, which states that the gravitational force between two masses $ M $ and $ m $ separated by a distance $ r $ is given by:  

$$F_g = \frac{G M m}{r^2}$$

where:  
- $G$ is the **gravitational constant**, approximately $6.674 \times 10^{-11} \, \text{m}^3 \text{kg}^{-1} \text{s}^{-2}$.  
- $M$ is the mass of the **central body** (e.g., the Sun or Earth).  
- $m$ is the mass of the **orbiting body** (e.g., a planet or satellite).  
- $r$ is the **orbital radius** (distance between the two masses).  

Since the orbiting body follows a **circular** path, the gravitational force provides the necessary **centripetal force**, which is given by:  

$$F_c = \frac{m v^2}{r}$$

where $v$ is the **orbital velocity** of the body.  

Setting the gravitational force equal to the centripetal force:  

$$\frac{G M m}{r^2} = \frac{m v^2}{r}$$

Canceling $ m $ from both sides (since the mass of the orbiting body does not affect the motion):  

$$\frac{G M}{r^2} = \frac{v^2}{r}$$

Rearranging:  

$$v^2 = \frac{G M}{r}$$

Since the orbital period $ T $ is related to velocity by the equation:  

$$v = \frac{2\pi r}{T}$$

substituting for $v$:  

$$\left(\frac{2\pi r}{T}\right)^2 = \frac{G M}{r}$$

Expanding the square:  

$$\frac{4\pi^2 r^2}{T^2} = \frac{G M}{r}$$

Multiplying both sides by $r$:  

$$4\pi^2 r^3 = G M T^2$$

Rearranging:  

$$T^2 = \frac{4\pi^2}{G M} r^3$$

This confirms **Kepler’s Third Law**:  

$$T^2 \propto r^3$$

The proportionality constant, $\frac{4\pi^2}{G M}$, depends only on the **mass of the central body**. This means that any two objects orbiting the same central mass will follow the same relationship between $T^2$ and $r^3$.  

---

## **3. Implications in Astronomy**  

### **3.1 Calculating Planetary Masses**  

One of the most useful applications of Kepler’s Third Law is in **determining the mass of a celestial body** when we know the orbital period and radius of a smaller body orbiting it.  

Rearranging the equation:  

$$M = \frac{4\pi^2 r^3}{G T^2}$$

we can estimate the **mass of Earth** using the Moon’s orbital parameters:  
- **Orbital radius**: $r \approx 3.84 \times 10^8$ m  
- **Orbital period**: $T \approx 27.3 (days) = 2.36\times 10^6$  

Substituting the values:  

$$M = \frac{4\pi^2 (3.84 \times 10^8)^3}{(6.674 \times 10^{-11}) (2.36 \times 10^6)^2}$$

Solving for $ M $, we obtain a value close to the **actual mass of Earth** ($5.97 \times 10^{24}$ kg).  

### **3.2 Exoplanet Detection**  

Kepler’s Third Law is crucial in **detecting and characterizing exoplanets**. By measuring a star’s periodic motion due to an orbiting planet (using the **radial velocity method**) or observing periodic dips in brightness (using the **transit method**), astronomers determine the planet’s orbital radius and period. This information allows them to estimate **planetary masses and distances**.  

### **3.3 Satellite Orbits and Space Missions**  

Kepler’s Third Law is applied in designing **satellite orbits**. For example:  
- **GPS satellites** orbit Earth at a specific radius to synchronize their periods with Earth’s rotation.  
- **Geostationary satellites** have an orbital radius such that their period matches Earth’s 24-hour day, making them appear stationary in the sky.  

---

## **4. Computational Simulation**  

To verify the relationship between orbital period and radius, we simulate circular orbits for different values of $r$ and plot $T^2$ versus $r^3$.  

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.674e-11  # Gravitational constant
M = 5.97e24    # Mass of Earth

# Define orbital radii (m)
radii = np.linspace(7e6, 5e7, 100)  # From 7000 km to 50000 km

# Compute orbital periods (s)
T = np.sqrt((4 * np.pi**2 * radii**3) / (G * M))

# Plot T^2 vs. r^3
plt.figure(figsize=(8,6))
plt.plot(radii**3, T**2, label='Simulation Data', color='b')
plt.xlabel('Orbital Radius^3 (m^3)')
plt.ylabel('Orbital Period^2 (s^2)')
plt.title('Kepler’s Third Law: T² vs r³')
plt.legend()
plt.grid()
plt.show()
```
[Colab](https://colab.research.google.com/drive/1UVTQJm3-aR74L4xRO0jY-iTIrj3-3xBv?authuser=1)
![Example Image](https://github.com/mirsaddoyan/solutions_repo/blob/main/docs/1%20Physics/2%20Gravity/Unknown-10.png?raw=true)
The graph should be a straight line, confirming that **$T^2 \propto r^3$**.  

---

## **5. Extensions to Elliptical Orbits**  

For **elliptical orbits**, Kepler’s Third Law still applies, but we replace $r$ with the **semi-major axis** $a$:  

$$T^2 = \frac{4\pi^2}{G M} a^3$$

This accounts for planets, asteroids, and comets with non-circular orbits.  

---

## **6. Conclusion**  

Kepler’s Third Law provides a fundamental connection between orbital period and radius, shaping our understanding of celestial mechanics. From planetary science to satellite engineering, its applications span vast areas of physics and astronomy. By deriving and verifying the law through computational simulations, we confirm its accuracy and usefulness in real-world scenarios.
