import streamlit as st
from datetime import date

def calculate_school_years(birth_year, birth_month):
    """
    生年月日から小学校から大学までの入学・卒業年度と月を計算します。
    日本の一般的な学齢に基づいて計算しています。
    """
    years = {}

    # 小学校
    # 6歳の誕生日を迎える年度の4月に入学
    elementary_school_start_age = 6
    elementary_entrance_year = birth_year + elementary_school_start_age
    
    # 4月2日以降の生まれは翌年度入学
    if birth_month >= 4:
        elementary_entrance_year += 1
    
    elementary_graduation_year = elementary_entrance_year + 6

    years['小学校'] = {
        '入学年': elementary_entrance_year,
        '入学月': 4, # 小学校の入学は通常4月
        '卒業年': elementary_graduation_year,
        '卒業月': 3  # 小学校の卒業は通常3月
    }

    # 中学校
    junior_high_entrance_year = elementary_graduation_year
    junior_high_graduation_year = junior_high_entrance_year + 3
    years['中学校'] = {
        '入学年': junior_high_entrance_year,
        '入学月': 4, # 中学校の入学は通常4月
        '卒業年': junior_high_graduation_year,
        '卒業月': 3  # 中学校の卒業は通常3月
    }

    # 高校
    high_school_entrance_year = junior_high_graduation_year
    high_school_graduation_year = high_school_entrance_year + 3
    years['高校'] = {
        '入学年': high_school_entrance_year,
        '入学月': 4, # 高校の入学は通常4月
        '卒業年': high_school_graduation_year,
        '卒業月': 3  # 高校の卒業は通常3月
    }

    # 大学（4年制）
    university_entrance_year = high_school_graduation_year
    university_graduation_year = university_entrance_year + 4
    years['大学'] = {
        '入学年': university_entrance_year,
        '入学月': 4, # 大学の入学は通常4月
        '卒業年': university_graduation_year,
        '卒業月': 3  # 大学の卒業は通常3月
    }

    return years

st.set_page_config(page_title="入学・卒業年度計算アプリ", layout="centered")

st.title("🎓 生年月日から入学・卒業年度を計算")

st.write("あなたの生年月日を入力してください。小学校から大学までの入学・卒業年度と月を計算します。")

# 入力フォーム
col1, col2 = st.columns(2)
with col1:
    birth_year = st.number_input("生まれた年", min_value=1900, max_value=date.today().year, value=2000, step=1)
with col2:
    birth_month = st.slider("生まれた月", min_value=1, max_value=12, value=4)

if st.button("計算する"):
    if birth_year and birth_month:
        st.subheader(f"{birth_year}年{birth_month}月生まれの方の学歴")
        
        school_years = calculate_school_years(birth_year, birth_month)

        for school_name, dates in school_years.items():
            st.markdown(f"---")
            st.write(f"### {school_name}")
            st.write(f"**入学:** {dates['入学年']}年{dates['入学月']}月")
            st.write(f"**卒業:** {dates['卒業年']}年{dates['卒業月']}月")
        st.success("計算が完了しました！")
    else:
        st.error("生まれた年と月を入力してください。")

st.markdown("""
---
<small>※日本の一般的な学齢に基づいて計算しています。4月2日生まれから翌年4月1日生まれまでが同じ学年として扱われます。入学は4月、卒業は3月としています。</small>
""", unsafe_allow_html=True)
