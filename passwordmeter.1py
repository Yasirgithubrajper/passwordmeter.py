import re
import streamlit as st
import random
import string

def generate_strong_password():
    # Generate a strong password with at least 8 characters, including uppercase, lowercase, digits, and special characters
    length = 12
    characters = string.ascii_letters + string.digits + "!@#$%^&*"
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def check_password_strength(password):
    score = 0
    feedback = []

    # Length Check
    if len(password) >= 8:
        score += 1
    else:
        feedback.append("❌ Password should be at least 8 characters long.")
    
    # Upper & Lowercase Check
    if re.search(r"[A-Z]", password) and re.search(r"[a-z]", password):
        score += 1
    else:
        feedback.append("❌ Include both uppercase and lowercase letters.")
    
    # Digit Check
    if re.search(r"\d", password):
        score += 1
    else:
        feedback.append("❌ Add at least one number (0-9).")
    
    # Special Character Check
    if re.search(r"[!@#$%^&*]", password):
        score += 1
    else:
        feedback.append("❌ Include at least one special character (!@#$%^&*).")
    
    # Strength Rating
    if score == 4:
        feedback.append("✅ Strong Password!")
    elif score == 3:
        feedback.append("⚠️ Moderate Password - Consider adding more security features.")
    else:
        feedback.append("❌ Weak Password - Improve it using the suggestions above.")
    
    return score, feedback

def main():
    st.title("🔐 Password Strength Meter")
    st.write("Check the strength of your password and get suggestions to improve it.")

    # Password input
    password = st.text_input("Enter your password:", type="password")

    if st.button("Check Strength"):
        if password:
            score, feedback = check_password_strength(password)
            for message in feedback:
                st.write(message)
        else:
            st.write("Please enter a password to check its strength.")

    # Password generator
    st.write("### 🛠️ Generate a Strong Password")
    if st.button("Generate Password"):
        strong_password = generate_strong_password()
        st.write(f"Generated Password: `{strong_password}`")
        st.write("Copy this password and use it for a secure account.")

if __name__ == "__main__":
    main()
