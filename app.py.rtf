{\rtf1\ansi\ansicpg1252\cocoartf2709
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 import streamlit as st\
import anthropic\
import stripe\
\
# 1. Page Configuration & Title\
st.set_page_config(page_title="Breath and Bone Front Matter Suite", page_icon="\uc0\u55357 \u56538 ", layout="centered")\
\
st.title("\uc0\u55357 \u56538  Breath & Bone Book Front Matter Suite")\
st.write("Generate professional, industry-standard copyright pages and library-compliant P-CIP blocks instantly.")\
\
# 2. Secure Secret Key Setup (Configured in Streamlit Cloud Dashboard)\
try:\
    stripe.api_key = st.secrets["STRIPE_SECRET_KEY"]\
    anthropic_key = st.secrets["ANTHROPIC_API_KEY"]\
    PRICE_ID = st.secrets["STRIPE_PRICE_ID"]\
    client = anthropic.Anthropic(api_key=anthropic_key)\
except Exception:\
    st.error("Configuration Error: API Keys are missing from production environment secrets.")\
    st.stop()\
\
# 3. Create Tabs\
tab1, tab2 = st.tabs(["\uc0\u10024  Front Matter Generator", "\u55357 \u56589  CIP Validator"])\
\
with tab1:\
    st.subheader("Step 1: Enter Your Book Metadata")\
    \
    # Form layout\
    with st.form("metadata_form"):\
        col1, col2 = st.columns(2)\
        with col1:\
            title = st.text_input("Main Book Title*", placeholder="e.g., The Midnight Chronology")\
            author = st.text_input("Author Name*", placeholder="e.g., Jane Doe")\
            publisher = st.text_input("Imprint/Publisher Name*", placeholder="e.g., Breath and Bone Books")\
        with col2:\
            subtitle = st.text_input("Subtitle (Optional)", placeholder="e.g., A Time Travel Adventure")\
            pub_year = st.text_input("Publication Year*", placeholder="2026")\
            pub_city = st.text_input("Publication City & State*", placeholder="e.g., Atlanta, GA")\
            \
        genre = st.selectbox("Book Genre/Category*", ["Fiction", "Non-Fiction/Memoir", "Self-Help/Advice/Finance"])\
        \
        st.markdown("---")\
        include_cip = st.checkbox("\uc0\u55357 \u56960  Upgrade: Include Library P-CIP Block (\\$25.00 USD)", value=False)\
        \
        # Hidden CIP Fields (Only processed if checked)\
        st.caption("Fill these out ONLY if you selected the P-CIP Upgrade above:")\
        isbn_paper = st.text_input("ISBN-13 (Paperback)")\
        isbn_ebook = st.text_input("ISBN-13 (Ebook)")\
        lccn = st.text_input("LCCN (If unavailable, leave blank)")\
        summary = st.text_area("Brief Book Summary (2-3 sentences for library indexing)")\
\
        # Mandatory Terms Checkbox\
        legal_check = st.checkbox("I agree that this tool is an automated assistant. I accept 100% responsibility for proofreading my final layouts prior to printing.")\
\
        submit = st.form_submit_button("Generate My Front Matter")\
\
    # 4. Processing Engine Logic\
    if submit:\
        if not title or not author or not publisher or not pub_year or not pub_city:\
            st.error("\uc0\u10060  Please fill in all required fields marked with an asterisk (*).")\
        elif not legal_check:\
            st.error("\uc0\u10060  You must check the validation and terms waiver box to proceed.")\
        else:\
            # Generate the baseline Free Copyright Component\
            disclaimer = ""\
            if genre == "Fiction":\
                disclaimer = "This is a work of fiction. Names, characters, places, and incidents are products of the author\'92s imagination or are used fictitiously."\
            elif genre == "Non-Fiction/Memoir":\
                disclaimer = "The events and conversations in this book reflect the author\'92s best recollections. The author has made every effort to ensure accuracy."\
            else:\
                disclaimer = "The information in this book is for educational purposes only. It should not be treated as professional medical, financial, or legal advice."\
\
            free_copyright_text = f"""Copyright \'a9 \{pub_year\} by \{author\}\
All rights reserved. No part of this book may be reproduced or transmitted in any form or by any means without written permission from the publisher, except for brief quotations in reviews.\
\
Published by \{publisher\}\
\{pub_city\}\
://yourimprintlink.com (Placeholder)\
\
\{disclaimer\}\
"""\
\
            # Scenario A: Free Copyright Only\
            if not include_cip:\
                st.success("\uc0\u55356 \u57225  Your Free Copyright Page is ready!")\
                st.text_area("Copy and paste this into your manuscript layout:", free_copyright_text, height=250)\
            \
            # Scenario B: Paid Copyright + CIP Block\
            else:\
                st.warning("\uc0\u55357 \u56499  Payment Required for P-CIP Processing.")\
                try:\
                    # Create a seamless Stripe Checkout session URL\
                    checkout_session = stripe.checkout.Session.create(\
                        payment_method_types=['card'],\
                        line_items=[\{'price': PRICE_ID, 'quantity': 1\}],\
                        mode='payment',\
                        success_url=st.query_params.get("success", "https://streamlit.io") + "?paid=true",\
                        cancel_url=st.query_params.get("cancel", "https://streamlit.io"),\
                    )\
                    st.markdown(f"[\uc0\u55357 \u56599  Click Here to Securely Pay \\$25.00 via Stripe to Unlock CIP](\{checkout_session.url\})", unsafe_allow_html=True)\
                except Exception as e:\
                    st.error(f"Stripe Integration Error: \{e\}")\
\
    # Handle incoming redirect after a successful Stripe payment loop\
    if st.query_params.get("paid") == "true":\
        st.success("\uc0\u55357 \u56499  Payment Verified! Creating your standard library P-CIP Block...")\
        \
        # Build strict system call to Claude 3.5 Haiku\
        prompt = f"""You are an elite academic library cataloger. Generate a Publisher's Cataloging-in-Publication (P-CIP) block.\
        Title: \{title\} \{" : " + subtitle if subtitle else ""\}\
        Author: \{author\}\
        Publisher: \{publisher\}\
        Year: \{pub_year\}\
        City/State: \{pub_city\}\
        ISBN Paperback: \{isbn_paper\}\
        ISBN Ebook: \{isbn_ebook\}\
        LCCN: \{lccn if lccn else "Unavailable"\}\
        Summary: \{summary\}\
\
        Follow AACR2, RDA, and Library of Congress formatting parameters strictly. Use proper block margins, indents, double dashes (--), and structural punctuation. Output ONLY the raw block text inside a clean monospaced layout. Zero pleasantries. Zero preamble."""\
\
        with st.spinner("Analyzing data models and structural matrices..."):\
            try:\
                response = client.messages.create(\
                    model="claude-3-5-haiku-20241022",\
                    max_tokens=800,\
                    temperature=0.0,\
                    messages=[\{"role": "user", "content": prompt\}]\
                )\
                cip_block = response.content[0].text\
                \
                st.subheader("Your Full Premium Front Matter Bundle:")\
                final_combined = f"\{free_copyright_text\}\\n\\n" + "\uc0\u9472 " * 40 + f"\\n\\n\{cip_block\}"\
                st.text_area("Copy your combined files below:", final_combined, height=500)\
            except Exception as api_err:\
                st.error(f"AI Matrix Timeout: \{api_err\}")\
\
with tab2:\
    st.subheader("\uc0\u55357 \u56523  Rule-Based CIP Layout Validator")\
    st.write("Before sending your manuscript files to print, paste your final text string below to perform structural sanity diagnostics.")\
    \
    paste_box = st.text_area("Paste code block here:", height=300)\
    if st.button("Run Diagnostic Scanning"):\
        if not paste_box:\
            st.error("Please enter a text string to scan.")\
        else:\
            errors = []\
            # Check 1: Check for standard library double dashes\
            if "--" not in paste_box:\
                errors.append("\uc0\u9888 \u65039  Missing element transitions: Standard library segments require explicit spacing double dashes (`--`).")\
            # Check 2: Core numerical structure verification\
            if "ISBN" not in paste_box.upper():\
                errors.append("\uc0\u9888 \u65039  Missing asset registry markers: The system cannot locate explicit labeled ISBN tokens.")\
            \
            if not errors:\
                st.success("\uc0\u9989  Structural Sanity Checks Passed! Structural alignments match system benchmarks.")\
            else:\
                for err in errors:\
                    st.markdown(err)\
}