# chemunitcal.
AVOGADRO_NUMBER = 6.022e23  
STP_VOLUME = 22.4  

# ฟังก์ชันแปลงหน่วย
def grams_to_moles(mass, molar_mass):
    return mass / molar_mass

def moles_to_grams(moles, molar_mass):
    return moles * molar_mass

def particles_to_moles(particles):
    return particles / AVOGADRO_NUMBER

def moles_to_particles(moles):
    return moles * AVOGADRO_NUMBER

def volume_stp_to_moles(volume):
    return volume / STP_VOLUME

def moles_to_volume_stp(moles):
    return moles * STP_VOLUME

# UI ของเว็บแอป
st.title("Chemical Unit Converter ⚗️")

option = st.selectbox("เลือกประเภทการแปลงหน่วย", [
    "แปลงกรัมเป็นโมล",
    "แปลงโมลเป็นกรัม",
    "แปลงอนุภาคเป็นโมล",
    "แปลงโมลเป็นอนุภาค",
    "แปลงปริมาตร STP เป็นโมล",
    "แปลงโมลเป็นปริมาตร STP"
])

if option == "แปลงกรัมเป็นโมล":
    mass = st.number_input("ป้อนมวล (กรัม)", min_value=0.0)
    molar_mass = st.number_input("ป้อนมวลโมลาร์ (g/mol)", min_value=0.1)
    if st.button("คำนวณ"):
        result = grams_to_moles(mass, molar_mass)
        st.success(f"ผลลัพธ์: {result:.4f} โมล")

elif option == "แปลงโมลเป็นกรัม":
    moles = st.number_input("ป้อนจำนวนโมล", min_value=0.0)
    molar_mass = st.number_input("ป้อนมวลโมลาร์ (g/mol)", min_value=0.1)
    if st.button("คำนวณ"):
        result = moles_to_grams(moles, molar_mass)
        st.success(f"ผลลัพธ์: {result:.4f} กรัม")

elif option == "แปลงอนุภาคเป็นโมล":
    particles = st.number_input("ป้อนจำนวนอนุภาค", min_value=0.0, format="%.2e")
    if st.button("คำนวณ"):
        result = particles_to_moles(particles)
        st.success(f"ผลลัพธ์: {result:.4e} โมล")

elif option == "แปลงโมลเป็นอนุภาค":
    moles = st.number_input("ป้อนจำนวนโมล", min_value=0.0)
    if st.button("คำนวณ"):
        result = moles_to_particles(moles)
        st.success(f"ผลลัพธ์: {result:.4e} อนุภาค")

elif option == "แปลงปริมาตร STP เป็นโมล":
    volume = st.number_input("ป้อนปริมาตรที่ STP (ลิตร)", min_value=0.0)
    if st.button("คำนวณ"):
        result = volume_stp_to_moles(volume)
        st.success(f"ผลลัพธ์: {result:.4f} โมล")

elif option == "แปลงโมลเป็นปริมาตร STP":
    moles = st.number_input("ป้อนจำนวนโมล", min_value=0.0)
    if st.button("คำนวณ"):
        result = moles_to_volume_stp(moles)
        st.success(f"ผลลัพธ์: {result:.4f} ลิตรที่ STP")
