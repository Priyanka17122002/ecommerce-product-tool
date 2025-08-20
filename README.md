# Internal Product Management Tool (eCommerce)

This repo contains:
1) **Step 1 – Database Design** → `erd.md`
2) **Step 2 – Class Design** → `class_diagram.md`
3) **Step 3 – Implementation (Django)** → code under `config/` and `catalog/`

## Tech
- Python, Django
- Django Admin for CRUD
- Mermaid for diagrams (renders on GitHub)

## Run locally

```bash
# 1) create venv
python -m venv .venv
# 2) activate
# Windows:
.venv\Scripts\activate
# macOS/Linux:
# source .venv/bin/activate

# 3) install
pip install django

# 4) migrate
python manage.py migrate

# 5) create admin user
python manage.py createsuperuser

# 6) run
python manage.py runserver
