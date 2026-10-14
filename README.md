def convert_temperature(value, from_unit, to_unit):
    units = {"C", "F", "K"}

    if from_unit not in units or to_unit not in units:
        raise ValueError("Units must be C, F, or K")

    # Convert the input to Celsius first.
    if from_unit == "C":
        celsius = value
    elif from_unit == "F":
        celsius = (value - 32) * 5 / 9
    else:
        celsius = value - 273.15

    if celsius < -273.15:
        raise ValueError("Temperature is below absolute zero")

    if to_unit == "C":
        return celsius
    elif to_unit == "F":
        return celsius * 9 / 5 + 32
    else:
        return celsius + 273.15


if __name__ == "__main__":
    print("25°C in Fahrenheit:", round(convert_temperature(25, "C", "F"), 2))
    print("77°F in Kelvin:", round(convert_temperature(77, "F", "K"), 2))
    print("300 K in Celsius:", round(convert_temperature(300, "K", "C"), 2))
