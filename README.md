# Ctrl-C-Ctrl-V
hi sloth it is my code
def keyboardShortcut(sentence):
    words = sentence.split()
    result = []
    copied_text = ""
    buffer = []  # Temporary storage for words before each 'Ctrl + C'
    
    for word in words:
        if word == "Ctrl":
            # Ignore + and check for 'C' or 'V' in next positions
            continue
        elif word == "+":  # skip the "+" in Ctrl + C or Ctrl + V
            continue
        elif word == "C":  # Ctrl + C
            copied_text = " ".join(buffer)  # Update copied text to everything behind
        elif word == "V":  # Ctrl + V
            if copied_text:
                result.append(copied_text)  # Append copied text to result if it exists
        else:
            # Any regular word
            result.append(word)
            buffer.append(word)  # Keep adding to buffer until "Ctrl + C" overwrites it
    
    # Join result words to form the final sentence
    return " ".join(result)

# Test cases
print(keyboardShortcut("the egg and Ctrl + C Ctrl + V the spoon"))  # Output: "the egg and the egg and the spoon"
print(keyboardShortcut("WARNING Ctrl + V Ctrl + C Ctrl + V"))  # Output: "WARNING WARNING"
print(keyboardShortcut("The Ctrl + C Ctrl + V Town Ctrl + C Ctrl + V"))  # Output: "The The Town The The Town"
