def convert_temperature(temp, unit):
    if unit == 'F':
        converted_temp = (temp - 32) * 5/9
        converted_unit = 'Celsius'
    elif unit == 'C':
        converted_temp = (temp * 9/5) + 32
        converted_unit = 'Fahrenheit'
    else:
        return "Invalid unit. Please use 'F' for Fahrenheit or 'C' for Celsius."
    
    return round(converted_temp, 2), converted_unit

temp = float(input("Enter the temperature to convert: "))
unit = input("Enter the unit of the temperature ('F' for Fahrenheit, 'C' for Celsius): ").upper()
result = convert_temperature(temp, unit)
print(f"The converted temperature is {result[0]} {result[1]}")
Task 2
import openai

# Set up your OpenAI API key
openai.api_key = 'YOUR_API_KEY_HERE'

# Define prompts for zero-shot, few-shot, and chain-of-thought techniques
zero_shot_prompt = "Explain the concept of quantum entanglement."
few_shot_prompt = "To explain the concept of quantum entanglement, consider the following scenario: Two particles are created in an entangled state, meaning their properties are correlated regardless of the distance between them. This phenomenon was famously described as 'spooky action at a distance' by Einstein. Now, elaborate on how this phenomenon is utilized in quantum computing."
chain_of_thought_prompt = "Explain the concept of quantum entanglement. Now, imagine you're teaching this to a high school student who is curious about advanced physics but doesn't have a background in it. Simplify your explanation and provide relatable examples."

# Generate responses from the AI model for each prompt type
zero_shot_response = openai.Completion.create(
    engine="text-davinci-003",
    prompt=zero_shot_prompt,
    max_tokens=100
)

few_shot_response = openai.Completion.create(
    engine="text-davinci-003",
    prompt=few_shot_prompt,
    max_tokens=100
)

chain_of_thought_response = openai.Completion.create(
    engine="text-davinci-003",
    prompt=chain_of_thought_prompt,
    max_tokens=100
)

# Print out the responses
print("Zero-Shot Response:")
print(zero_shot_response.choices[0].text.strip())

print("\nFew-Shot Response:")
print(few_shot_response.choices[0].text.strip())

print("\nChain-of-Thought Response:")
print(chain_of_thought_response.choices[0].text.strip())

