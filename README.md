%env GEMINI_API_KEY=AIzaSyBrrHfNXLFYcyaN_IOJavhvaERllGjIlEw
!pip install -q transformers pillow google-generativeai
from google import  genai
import os
client = genai.Client()
if "GEMINI_API_KEY" not in os.environ:
    print("Please set your Gemini API Key in the envirnoment variable   GEMINI_API_KAY")
else:
    client=genai.Client()
    MODEL="gemini-2.5-flash"
    prompt=input("Enter your story prompt and press enter : \n")
if prompt.strip()=="":
  print("No prompt entered , Existing.")
else:
  print("Generating story for prompt:{prompt}")
  print("May take few seconds")
  try:
    resp=client.models.generate_content(model=MODEL,contents={prompt})
    print("\n-----Generated story-----\n")
    print(resp.text)
    
  except Exception as e:
    print(f"Error while generating story : {e}")
