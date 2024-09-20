import re

def check_password_strength(password):
    # Minimum criteria for strong password
    length_criteria = len(password) >= 8
    upper_criteria = re.search(r'[A-Z]', password) is not None
    lower_criteria = re.search(r'[a-z]', password) is not None
    digit_criteria = re.search(r'[0-9]', password) is not None
    special_criteria = re.search(r'[@$!%*?&]', password) is not None
    
    # Calculate the number of criteria met
    criteria_met = sum([length_criteria, upper_criteria, lower_criteria, digit_criteria, special_criteria])
    
    # Determine strength level
    if criteria_met < 3:
        return "Weak"
    elif criteria_met == 3:
        return "Okay"
    else:
        return "Strong"

# Input password from user
password = input("Enter a password to check its strength: ")
strength = check_password_strength(password)
print(f"Password strength: {strength}")
