
# Saldo_1 – webový generátor (Streamlit)

## Lokálny beh
```
pip install -r requirements.txt
streamlit run app_streamlit.py
```
Otvor sa URL (napr. http://localhost:8501), nahraj 4 Excely, vyplň polia a klikni "Generovať".

## Docker
```
docker build -t saldo-app .
docker run -p 8501:8501 saldo-app
```
Potom otvor http://localhost:8501

## Nasadenie
- **Streamlit Cloud**: nová app, prepoj Git repo, vyber `app_streamlit.py` a pridaj `requirements.txt`.
- **Hugging Face Spaces**: vytvor Space (Streamlit), nahraj tieto súbory, definuj `requirements.txt`.
- **VPS**: spusti Docker príkazy vyššie a daj nad to reverzný proxy (napr. Nginx) na vlastnej doméne.

---

## Samostatná PHP aplikácia

Repozitár obsahuje aj kompletne portovanú PHP verziu v adresári [`php_app/`](php_app/). Ide o samostatnú aplikáciu nezávislú od
Streamlit rozhrania.

### Rýchly štart

```bash
cd php_app
composer install
php -S 0.0.0.0:8080 -t public
```

Potom otvor prehliadač na adrese `http://localhost:8080` a nahraj rovnaké Excel podklady ako v pôvodnej aplikácii.

### Štruktúra

- `php_app/src/SaldoGenerator.php` – port logiky zo `saldo_core.py` postavený na PhpSpreadsheet a Dompdf.
- `php_app/public/index.php` – jednoduché HTML UI (bez závislosti na frameworku) pre nahratie súborov a spustenie generovania.
- `php_app/README.md` – podrobný opis inštalácie, štruktúry a používania PHP verzie.
