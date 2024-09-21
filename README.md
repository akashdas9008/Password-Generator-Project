# Password-Generator-Project
import random
import string

def generate_password(length=12):
    """Generate a random password of specified length."""
    if length < 8:
        raise ValueError("Password length should be at least 8 characters.")

    # Define the characters to choose from
    letters = string.ascii_letters
    digits = string.digits
    special_chars = string.punctuation

    # Combine all characters
    all_characters = letters + digits + special_chars

    # Ensure the password includes at least one of each type of character
    password = [
        random.choice(string.ascii_uppercase),
        random.choice(string.ascii_lowercase),
        random.choice(string.digits),
        random.choice(string.punctuation)
    ]

    # Fill the rest of the password length with random choices from all characters
    password += [random.choice(all_characters) for _ in range(length - 4)]

    # Shuffle the password list to ensure randomness
    random.shuffle(password)

    # Convert the list to a string
    return ''.join(password)

def main():
    print("Welcome to the Random Password Generator!")

    try:
        length = int(input("Enter the desired length of the password (minimum 8): "))
        if length < 8:
            raise ValueError("Password length should be at least 8 characters.")

        password = generate_password(length)
        print(f"Generated Password: {password}")

    except ValueError as e:
        print(f"Invalid input: {e}")

if __name__ == "__main__":
    main()
