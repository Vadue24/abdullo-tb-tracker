  GNU nano 7.2                                                                                                                         app.py                                                                                                                                  from flask import Flask, request, jsonify
from flask_cors import CORS
import psycopg2

app = Flask(__name__)
CORS(app)

# RDS Connection
conn = psycopg2.connect(
    host="db-abdullo.clyucs4e44b4.ap-northeast-2.rds.amazonaws.com",
    database="postgres",
    user="postgres",
    password="Abdullo121723"
)
cur = conn.cursor()

@app.route('/add', methods=['POST', 'GET'])
def add():
    if request.method == 'GET':
        return "Use POST to insert data into the database."

    cur.execute("""
        INSERT INTO tbl_abdullo_tuberculosis (
            Country, Region, Income_Level, Year, TB_Cases, TB_Deaths,
            TB_Incidence_Rate, TB_Mortality_Rate, TB_Treatment_Success_Rate,
            Drug_Resistant_TB_Cases, HIV_CoInfected_TB_Cases, Population,
            GDP_Per_Capita, Health_Expenditure_Per_Capita, Urban_Population_Percentage,
            Malnutrition_Prevalence, Smoking_Prevalence, TB_Doctors_Per_100K,
            TB_Hospitals_Per_Million, Access_To_Health_Services,
            BCG_Vaccination_Coverage, HIV_Testing_Coverage
        )
        VALUES ('TestCountry', 'TestRegion', 'Low', 2024, 1000, 50, 10.5, 1.2, 80.0,
                20, 10, 1000000, 5000, 300, 70.5, 12.0, 15.0, 5.5, 2.0, 80.0, 90.0, 85.0)
    """)
    conn.commit()
    return "1 row added!"


@app.route('/delete', methods=['POST', 'GET'])
def delete():
    if request.method == 'GET':
        return "Use POST to delete data from the database."

    data = request.get_json()
    row_id = data.get('id')

    if row_id is None:
        return "Missing 'id' in request", 400

    try:
        cur.execute("DELETE FROM tbl_abdullo_tuberculosis WHERE id = %s", (row_id,))
        conn.commit()
        return f"Row with ID {row_id} deleted!"
    except Exception as e:
        return str(e), 500


@app.route('/records', methods=['GET'])
def records():
    cur.execute("SELECT id, Country, Year FROM tbl_abdullo_tuberculosis ORDER BY id")
    rows = cur.fetchall()
    result = [{"id": r[0], "country": r[1], "year": r[2]} for r in rows]
    return jsonify(result)


if __name__ == '__main__':
    app.run(host='0.0.0.0', port=80)
