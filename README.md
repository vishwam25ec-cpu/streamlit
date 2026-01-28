import pandas as pd
import streamlit as st

st.title("My first streamlit app")
st.write("Hello streamlit")

st.subheader("Section 1: Basic Input")
name1 = st.text_input("Enter your name", key="name1")
age1 = st.number_input("Enter your age", min_value=1, key="age1")

if st.button("Submit", key="btn1"):
    st.write("Name:",name1)
    st.write("age:",age1)
st.divider() 

#section 2:static table
st.subheader("section 2: static student table")
students = [
    {"name":"arun","age":19},
    {"name":"vinu","age":270}
]
st.table(students)

st.subheader("Section 3: Add Students (Persistent)")
name2 = st.text_input("Enter your name", key="name2")
age2 = st.number_input("Enter your age", min_value=1, key="age2")
if "student_list" not in st.session_state:
    st.session_state.student_list = []
if st.button("Submit", key="btn2"):
    if name2:
        st.session_state.student_list.append({"name": name2, "age": int(age2)})
        st.success("Student added")
    else:
        st.warning("Please enter a name")
st.table(st.session_state.student_list)

st.divider()

st.subheader("Section 4: Add Students (Persistent)")
