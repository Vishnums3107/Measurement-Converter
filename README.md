# Measurement-Converter
Measurement Converter that converts between various units like length, weight, temperature, and volume. The program will present a menu for the user to choose the type of conversion, then allow the user to input values for conversion.
# Conversion functions
def convert_length(value, from_unit, to_unit):
    conversions = {
        'm': {'km': value / 1000, 'cm': value * 100, 'mm': value * 1000, 'ft': value * 3.28084, 'in': value * 39.3701},
        'km': {'m': value * 1000, 'cm': value * 100000, 'mm': value * 1000000, 'ft': value * 3280.84, 'in': value * 39370.1},
        'cm': {'m': value / 100, 'km': value / 100000, 'mm': value * 10, 'ft': value * 0.0328084, 'in': value * 0.393701},
        'mm': {'m': value / 1000, 'km': value / 1000000, 'cm': value / 10, 'ft': value * 0.00328084, 'in': value * 0.0393701},
        'ft': {'m': value / 3.28084, 'km': value / 3280.84, 'cm': value * 30.48, 'mm': value * 304.8, 'in': value * 12},
        'in': {'m': value / 39.3701, 'km': value / 39370.1, 'cm': value * 2.54, 'mm': value * 25.4, 'ft': value / 12}
    }
    return conversions[from_unit][to_unit]

def convert_weight(value, from_unit, to_unit):
    conversions = {
        'kg': {'g': value * 1000, 'mg': value * 1000000, 'lb': value * 2.20462, 'oz': value * 35.274},
        'g': {'kg': value / 1000, 'mg': value * 1000, 'lb': value / 453.592, 'oz': value / 28.3495},
        'mg': {'kg': value / 1000000, 'g': value / 1000, 'lb': value / 453592, 'oz': value / 28349.5},
        'lb': {'kg': value / 2.20462, 'g': value * 453.592, 'mg': value * 453592, 'oz': value * 16},
        'oz': {'kg': value / 35.274, 'g': value * 28.3495, 'mg': value * 28349.5, 'lb': value / 16}
    }
    return conversions[from_unit][to_unit]

def convert_temperature(value, from_unit, to_unit):
    if from_unit == 'C' and to_unit == 'F':
        return (value * 9/5) + 32
    elif from_unit == 'C' and to_unit == 'K':
        return value + 273.15
    elif from_unit == 'F' and to_unit == 'C':
        return (value - 32) * 5/9
    elif from_unit == 'F' and to_unit == 'K':
        return (value - 32) * 5/9 + 273.15
    elif from_unit == 'K' and to_unit == 'C':
        return value - 273.15
    elif from_unit == 'K' and to_unit == 'F':
        return (value - 273.15) * 9/5 + 32
    return value  # If no conversion required

def convert_volume(value, from_unit, to_unit):
    conversions = {
        'l': {'ml': value * 1000, 'cl': value * 100, 'cm3': value * 1000, 'gal': value * 0.264172, 'floz': value * 33.814},
        'ml': {'l': value / 1000, 'cl': value / 10, 'cm3': value, 'gal': value / 3785.41, 'floz': value / 29.5735},
        'cl': {'l': value / 100, 'ml': value * 10, 'cm3': value * 10, 'gal': value / 378.541, 'floz': value / 29.5735},
        'cm3': {'l': value / 1000, 'ml': value, 'cl': value / 10, 'gal': value / 3785.41, 'floz': value / 29.5735},
        'gal': {'l': value / 0.264172, 'ml': value * 3785.41, 'cl': value * 378.541, 'cm3': value * 3785.41, 'floz': value * 128},
        'floz': {'l': value / 33.814, 'ml': value * 29.5735, 'cl': value * 2.95735, 'cm3': value * 29.5735, 'gal': value / 128}
    }
    return conversions[from_unit][to_unit]

# Main program loop
def measurement_converter():
    while True:
        print("\nWelcome to the Measurement Converter!")
        print("1. Length Conversion")
        print("2. Weight Conversion")
        print("3. Temperature Conversion")
        print("4. Volume Conversion")
        print("5. Exit")

        choice = input("Choose an option (1-5): ")

        if choice == '1':
            print("\nLength Conversion")
            value = float(input("Enter the value to convert: "))
            from_unit = input("From (m, km, cm, mm, ft, in): ").lower()
            to_unit = input("To (m, km, cm, mm, ft, in): ").lower()
            result = convert_length(value, from_unit, to_unit)
            print(f"{value} {from_unit} = {result} {to_unit}")

        elif choice == '2':
            print("\nWeight Conversion")
            value = float(input("Enter the value to convert: "))
            from_unit = input("From (kg, g, mg, lb, oz): ").lower()
            to_unit = input("To (kg, g, mg, lb, oz): ").lower()
            result = convert_weight(value, from_unit, to_unit)
            print(f"{value} {from_unit} = {result} {to_unit}")

        elif choice == '3':
            print("\nTemperature Conversion")
            value = float(input("Enter the value to convert: "))
            from_unit = input("From (C, F, K): ").upper()
            to_unit = input("To (C, F, K): ").upper()
            result = convert_temperature(value, from_unit, to_unit)
            print(f"{value} {from_unit} = {result} {to_unit}")

        elif choice == '4':
            print("\nVolume Conversion")
            value = float(input("Enter the value to convert: "))
            from_unit = input("From (l, ml, cl, cm3, gal, floz): ").lower()
            to_unit = input("To (l, ml, cl, cm3, gal, floz): ").lower()
            result = convert_volume(value, from_unit, to_unit)
            print(f"{value} {from_unit} = {result} {to_unit}")

        elif choice == '5':
            print("Exiting the program. Goodbye!")
            break

        else:
            print("Invalid choice! Please select a valid option.")

if __name__ == "__main__":
    measurement_converter()
