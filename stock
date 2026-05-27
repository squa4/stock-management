import streamlit as st
import pandas as pd
import yfinance as yf
import plotly.express as px

st.set_page_config(page_title="1억 만들기 프로젝트", layout="wide")

st.title("🚀 3년 내 1억 달성 프로젝트 대시보드")

# 사이드바: 종목 매수 입력 (앞에 # 추가)
st.sidebar.header("금주 매수 종목 입력")
ticker = st.sidebar.text_input("종목 코드 (예: AAPL, 005930.KS)")
amount = st.sidebar.number_input("매수 금액", min_value=0)
if st.sidebar.button("추가"):
    st.session_state['portfolio'] = st.session_state.get('portfolio', []) + [{'ticker': ticker, 'amount': amount}]

# 메인 화면: 수익률 분석 (앞에 # 추가)
if 'portfolio' in st.session_state:
    df = pd.DataFrame(st.session_state['portfolio'])
    st.write("### 현재 포트폴리오 상태")
    st.dataframe(df)

    # 데이터 시각화 (목표 달성률 예시)
    fig = px.pie(df, values='amount', names='ticker', title='자산 비중')
    st.plotly_chart(fig)

    st.info("실시간 수익률 연동을 위해서는 yfinance API를 통해 매주 종목 정보를 업데이트하세요.")
