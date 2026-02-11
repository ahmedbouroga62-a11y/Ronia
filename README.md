import streamlit as st

# إعدادات الصفحة (العنوان والأيقونة)
st.set_page_config(page_title="Ron.ia AI", page_icon="🤖")

st.title("Ron.ia AI 🤖")
st.markdown("مرحباً بك في واجهة Ron.ia الخاصة بك")

# إنشاء ذاكرة للمحادثة لكي لا تختفي الرسائل عند تحديث الصفحة
if "messages" not in st.session_state:
    st.session_state.messages = []

# عرض الرسائل السابقة من الذاكرة (مثل واجهات الشات الاحترافية)
for message in st.session_state.messages:
    with st.chat_message(message["role"]):
        st.markdown(message["content"])

# حقل إدخال النص (الذي يظهر في الأسفل دائماً)
if prompt := st.chat_input("كيف يمكنني مساعدتك اليوم؟"):
    # عرض رسالة المستخدم
    with st.chat_message("user"):
        st.markdown(prompt)
    st.session_state.messages.append({"role": "user", "content": prompt})

    # هنا تضع كود الذكاء الصناعي الخاص بـ Ron.ia
    # سنضع إجابة تجريبية حالياً
    response = f"Ron.ia: لقد استلمت رسالتك وهي: {prompt}" 

    # عرض رد Ron.ia
    with st.chat_message("assistant"):
        st.markdown(response)
    st.session_state.messages.append({"role": "assistant", "content": response})
