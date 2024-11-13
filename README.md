# Password_Checker

import string

def assess_password_strength(password):
  """Assesses the strength of a password based on various criteria.

  Args:
    password: The password to be assessed.

  Returns:
    A string indicating the password's strength.
  """

  length = len(password)
  has_uppercase = any(char.isupper() for char in password)
  has_lowercase = any(char.islower() for char in password)
  has_number  = any(char.isdigit() for char in password) 

  has_special_char = any(char not in string.ascii_letters + string.digits for char in password)

  strength = "Weak"
  if length >= 8 and has_uppercase and has_lowercase and has_number and has_special_char:
    strength = "Strong"
  elif length >= 8 and (has_uppercase or has_lowercase) and (has_number or has_special_char):
    strength = "Medium"

  return strength

if __name__ == "__main__":
  while True:
    password = input("Enter a password: ")
    strength = assess_password_strength(password)
    print("Password strength:", strength)
