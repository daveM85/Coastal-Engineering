#Calculate Wave Height
import math

def calculate_wave_height(U, F, d):
    """
    Calculate wave height using Wilson's Method.
    
    Parameters:
    U (float): Wind speed at 10m above the surface (m/s)
    F (float): Fetch length (m)
    d (float): Water depth (m)
    
    Returns:
    H (float): Wave height (m)
    """
    g = 9.81  # Acceleration due to gravity (m/s^2)
    
    # Calculate dimensionless parameters
    UF = (U**2) / (g * F)
    Ud = (U**2) / (g * d)
    
    # Empirical coefficients
    A = 0.283
    B = 0.53
    
    # Estimate wave height
    H = A * (UF**B) * (Ud**(1/3)) * F**(1/2)
    
    return H

# Example usage:
wind_speed = 15.0  # Wind speed (m/s)
fetch_length = 10000.0  # Fetch length (m)
water_depth = 50.0  # Water depth (m)

wave_height = calculate_wave_height(wind_speed, fetch_length, water_depth)
print(f"Estimated Wave Height: {wave_height:.2f} meters")
