# Building-a-strong-password-maker
def assess_password_strength(password):
  """Assesses the strength of a password based on various criteria.

  Args:
    password: The password to be assessed.

  Returns:
    A string indicating the password strength (e.g., "Weak", "Medium", "Strong").
  """

  length = len(password)
  has_uppercase = any(char.isupper() for char in password)
  has_lowercase = any(char.islower() for char in password)
  has_number = any(char.isdigit() for char in password)
  has_special_char = any(not char.isalnum() for char in password)

  criteria_met = 0
  if length >= 8:
    criteria_met += 1
  if has_uppercase:
    criteria_met += 1
  if has_lowercase:
    criteria_met += 1
  if has_number:
    criteria_met += 1
  if has_special_char:
    criteria_met += 1

  if criteria_met <= 2:
    return "Weak"
  elif criteria_met <= 4:
    return "Medium"
  else:
    return "Strong"

# Example usage:
password = input("Enter your password: ")
strength = assess_password_strength(password)
print("Password strength:", strength)
