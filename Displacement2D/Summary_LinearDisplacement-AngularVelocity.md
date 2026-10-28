# 2D body simulation.

## Sources.
[Mistral AI](https://chat.mistral.ai/chat/dcd1151b-4877-4cce-9f7f-29c57553cd8b)

## Summary.

In **2D**, the physics simplifies significantly compared to 3D. Here’s how the concepts of **displacement**, **angular velocity**, and the **inertia tensor** reduce in 2D:

---

---

## **1. Displacement**
In 2D, displacement is a **2D vector** \((x, y)\). The update equation remains the same as before, but only in the x and y directions:

\[
\Delta \vec{x} = \vec{v} \Delta t + \frac{1}{2} \vec{a} \Delta t^2
\]

- \(\vec{v} = (v_x, v_y)\) is the linear velocity.
- \(\vec{a} = (a_x, a_y)\) is the linear acceleration.
- \(\Delta \vec{x} = (\Delta x, \Delta y)\) is the displacement.

This is identical to the 3D case, but with only two components.

---

---

## **2. Angular Velocity**
In 2D, rotation is **only about the z-axis** (perpendicular to the plane). Thus:
- **Angular velocity** is a **scalar** \(\omega\) (not a vector).
- The direction of rotation is either **clockwise** (negative \(\omega\)) or **counterclockwise** (positive \(\omega\)).

The update for angular velocity is:
\[
\omega_{\text{new}} = \omega + \alpha \Delta t
\]
where \(\alpha\) is the **angular acceleration** (also a scalar in 2D).

---

---

## **3. Inertia Tensor in 2D**
In 2D, the inertia tensor reduces to a **single scalar**: the **moment of inertia** \(I\) about the z-axis (perpendicular to the plane). This is because rotation is only possible about this axis.

### **Moment of Inertia (Scalar)**
For a rigid body in 2D, the moment of inertia about the z-axis (passing through the center of mass) is:

\[
I = \int r^2 \, dm
\]
where:
- \(r\) is the perpendicular distance from the axis of rotation (z-axis) to the mass element \(dm\).
- In Cartesian coordinates: \(r^2 = x^2 + y^2\).

For a **discrete set of point masses** (e.g., a rocket modeled as a collection of parts):
\[
I = \sum_{i} m_i (x_i^2 + y_i^2)
\]
where:
- \(m_i\) is the mass of the \(i\)-th point.
- \((x_i, y_i)\) is the position of the \(i\)-th point relative to the center of mass.

---

### **Parallel Axis Theorem in 2D**
If you know the moment of inertia \(I_{\text{cm}}\) about the center of mass, and you want the moment of inertia about a parallel axis at a distance \(d\) from the center of mass, use:

\[
I = I_{\text{cm}} + M d^2
\]
where:
- \(M\) is the total mass.
- \(d\) is the perpendicular distance between the two axes.

---

### **Example: Moment of Inertia for Simple 2D Shapes**
| Shape               | Moment of Inertia (about center of mass) |
|---------------------|------------------------------------------|
| Point mass \(M\)    | \(I = M r^2\) (where \(r\) is distance from axis) |
| Thin rod (length \(L\)) | \(I = \frac{1}{12} M L^2\) (axis perpendicular to rod at center) |
| Solid disk (radius \(R\)) | \(I = \frac{1}{2} M R^2\) |
| Rectangular plate (width \(w\), height \(h\)) | \(I = \frac{1}{12} M (w^2 + h^2)\) |

---

---

## **4. Torque and Angular Acceleration in 2D**
In 2D, torque is also a **scalar** \(\tau\) (positive for counterclockwise, negative for clockwise). The relationship between torque, moment of inertia, and angular acceleration is:

\[
\tau = I \alpha
\]
where:
- \(\tau\) is the net torque.
- \(\alpha\) is the angular acceleration.

To compute the torque from a thruster:
\[
\tau_i = r_i \cdot F_i \cdot \sin(\theta_i)
\]
where:
- \(r_i\) is the distance from the thruster to the center of mass.
- \(F_i\) is the magnitude of the thruster force.
- \(\theta_i\) is the angle between the thruster’s force vector and the line connecting the thruster to the center of mass.

For multiple thrusters:
\[
\tau_{\text{net}} = \sum_{i} \tau_i
\]

Then, the angular acceleration is:
\[
\alpha = \frac{\tau_{\text{net}}}{I}
\]

---

---

## **5. Orientation Update in 2D**
In 2D, orientation is typically represented by a **single angle** \(\theta\) (e.g., the angle of the rocket relative to the x-axis). The update for \(\theta\) is:

\[
\theta_{\text{new}} = \theta + \omega \Delta t
\]

For small time steps, this is sufficient. For larger time steps or higher precision, you might use:
\[
\theta_{\text{new}} = \theta + \omega \Delta t + \frac{1}{2} \alpha \Delta t^2
\]

---

---

## **Summary for 2D Simulation**
| Concept               | 2D Representation                     | Update Equation                          |
|-----------------------|----------------------------------------|------------------------------------------|
| **Displacement**      | Vector \((x, y)\)                      | \(\Delta \vec{x} = \vec{v} \Delta t + \frac{1}{2} \vec{a} \Delta t^2\) |
| **Velocity**          | Vector \((v_x, v_y)\)                  | \(\vec{v}_{\text{new}} = \vec{v} + \vec{a} \Delta t\) |
| **Angular Velocity**  | Scalar \(\omega\)                      | \(\omega_{\text{new}} = \omega + \alpha \Delta t\) |
| **Orientation**       | Scalar \(\theta\)                      | \(\theta_{\text{new}} = \theta + \omega \Delta t\) |
| **Inertia Tensor**    | Scalar \(I\) (moment of inertia)      | \(I = \sum m_i (x_i^2 + y_i^2)\)         |
| **Torque**            | Scalar \(\tau\)                        | \(\tau = I \alpha\)                     |
| **Angular Acceleration** | Scalar \(\alpha\)                  | \(\alpha = \frac{\tau_{\text{net}}}{I}\) |

---

---
## **Pseudocode for 2D Rocket Simulation**
```python
# Initialize
x, y = 0, 0          # Position
vx, vy = 0, 0        # Linear velocity
theta = 0             # Orientation angle
omega = 0             # Angular velocity
I = compute_moment_of_inertia()  # Moment of inertia about CoM

# For each frame:
Fx_net, Fy_net = 0, 0  # Net force in x and y
tau_net = 0            # Net torque

for each thruster:
    Fx, Fy = thrust * cos(thruster_angle), thrust * sin(thruster_angle)
    Fx_net += Fx
    Fy_net += Fy
    # Torque: r_x * Fy - r_y * Fx (cross product in 2D)
    tau_net += (thruster_x * Fy - thruster_y * Fx)

# Linear motion
ax = Fx_net / mass
ay = Fy_net / mass
vx += ax * dt
vy += ay * dt
x += vx * dt + 0.5 * ax * dt**2
y += vy * dt + 0.5 * ay * dt**2

# Angular motion
alpha = tau_net / I
omega += alpha * dt
theta += omega * dt
```

---
**Would you like help computing the moment of inertia for your specific rocket geometry, or do you want to see a full code implementation for the 2D simulation?**