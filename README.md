# Password_Generator
```python
import random
import string

def generate_password(length):
    characters = string.ascii_letters + string.digits + string.punctuation
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def check_password_strength(password):
    score = 0
    criteria = {
        'contains_upper': False,
        'contains_lower': False,
        'contains_digit': False,
        'contains_special': False,
        'is_lengthy': False
    }
    
    if any(char.isupper() for char in password):
        score += 1
        criteria['contains_upper'] = True
    
    if any(char.islower() for char in password):
        score += 1
        criteria['contains_lower'] = True
    
    if any(char.isdigit() for char in password):
        score += 1
        criteria['contains_digit'] = True
    
    if any(char in string.punctuation for char in password):
        score += 1
        criteria['contains_special'] = True
    
    if len(password) >= 8:
        score += 1
        criteria['is_lengthy'] = True
    
    return score, criteria

# Prompt user for desired password length
length = int(input("Enter the desired password length: "))

# Generate and print the password
password = generate_password(length)
print("Generated password:", password)

# Check the strength of the password
password_strength, password_criteria = check_password_strength(password)
print("Password Strength:", password_strength)
for criterion, is_met in password_criteria.items():
    print(criterion.replace('_', ' ').title() + ':', 'Met' if is_met else 'Not Met')
```
