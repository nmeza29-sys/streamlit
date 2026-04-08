import streamlit as st
import random

st.title("What should I eat?")
st.write("Pick a mood and I decide for you")

mood = st.selectbox(
    "How are you feeling?",
    ["I want something fast", "I want something healthy", "I want comfort food", "I want something fun"]
)

hungry = st.slider("How hungry are you?", 1, 10, 5)

if mood == "I want something fast":
    foods = ["sandwich", "wrap", "pizza", "burger", "quesadilla"]
elif mood == "I want something healthy":
    foods = ["salad", "poke bowl", "grilled chicken", "soup", "rice bowl"]
elif mood == "I want comfort food":
    foods = ["pasta", "mac and cheese", "ramen", "mashed potatoes", "grilled cheese"]
else:
    foods = ["tacos", "sushi", "nachos", "dumplings", "crepes"]

if hungry <= 3:
    size = "small"
elif hungry <= 7:
    size = "medium"
else:
    size = "big"

if st.button("Decide for me"):
    choice = random.choice(foods)
    st.success("You should eat: " + size + " " + choice)
    st.write("No more overthinking. This is your food.")

st.write("---")
st.write("Extra button if you still can't decide")

if st.button("Pick something totally random"):
    all_foods = [
        "pizza", "salad", "burger", "sushi", "pasta",
        "tacos", "wrap", "ramen", "soup", "quesadilla"
    ]
    st.info("Okay fine. Eat: " + random.choice(all_foods))

st.caption("Very simple food picker app made with Streamlit")
