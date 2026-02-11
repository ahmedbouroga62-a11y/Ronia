import streamlit as st

st.set_page_config(page_title="Ron.ia AI", page_icon="🤖")

st.title("Ron.ia AI 🤖")
st.markdown("مرحباً بك في واجهة Ron.ia المساعد الذكي 


if "messages" not in st.session_state:
    st.session_state.messages = []


for message in st.session_state.messages:
    with st.chat_message(message["role"]):
        st.markdown(message["content"])


if prompt := st.chat_input("كيف يمكنني مساعدتك اليوم؟"):
    
    with st.chat_message("user"):
        st.markdown(prompt)
    st.session_state.messages.append({"role": "user", "content": prompt})

    
    response = f"Ron.ia: لقد استلمت رسالتك وهي: {prompt}" 

    # عرض رد Ron.ia
    with st.chat_message("assistant"):
        st.markdown(response)
    st.session_state.messages.append({"role": "assistant", "content": response})
