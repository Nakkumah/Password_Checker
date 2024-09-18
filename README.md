import re

def check_password_strength(password):
    # Criteria for a strong password
    length_criteria = len(password) >= 8
    digit_criteria = re.search(r"\d", password) is not None
    uppercase_criteria = re.search(r"[A-Z]", password) is not None
    lowercase_criteria = re.search(r"[a-z]", password) is not None
    symbol_criteria = re.search(r"[!@#$%^&*(),.?\":{}|<>]", password) is not None

    # Calculate strength score
    strength_score = sum([length_criteria, digit_criteria, uppercase_criteria, lowercase_criteria, symbol_criteria])

    # Provide feedback based on the strength score
    if strength_score == 5:
        return "Strong password! You're good to go."
    elif 3 <= strength_score < 5:
        return "Moderate password. Consider adding more symbols, digits, or uppercase letters."
    else:
        return "Weak password. Use at least 8 characters, including digits, uppercase, lowercase letters, and symbols."

# Example usage
password = input("Enter a password to check its strength: ")
print(check_password_strength(password))
