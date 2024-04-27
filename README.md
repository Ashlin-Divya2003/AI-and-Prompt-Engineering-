def convert_temperature(temp, unit):
    if unit == 'F':
        converted_temp = (temp - 32) * 5/9
        converted_unit = 'Celsius'
    elif unit == 'C':
        converted_temp = (temp * 9/5) + 32
        converted_unit = 'Fahrenheit'
    else:
        return "Invalid unit. Please use 'F' for Fahrenheit or 'C' for Celsius."
    
    return round(converted_temp, 2), converted_unit

temp = float(input("Enter the temperature to convert: "))
unit = input("Enter the unit of the temperature ('F' for Fahrenheit, 'C' for Celsius): ").upper()
result = convert_temperature(temp, unit)
print(f"The converted temperature is {result[0]} {result[1]}")
