# Test-Repository-
FFTLLP
from flask import Flask, render_template, request, redirect

app = Flask(__name__)

# Define routes

@app.route('/')
def home():
    return render_template('index.html')

@app.route('/about')
def about():
    return render_template('about.html')

@app.route('/products')
def products():
    # Logic to fetch and display products from the database
    products = fetch_products_from_database()
    return render_template('products.html', products=products)

@app.route('/contact', methods=['GET', 'POST'])
def contact():
    if request.method == 'POST':
        # Logic to handle form submission and send email
        name = request.form.get('name')
        email = request.form.get('email')
        message = request.form.get('message')
        send_email(name, email, message)
        return redirect('/thank-you')
    return render_template('contact.html')

@app.route('/thank-you')
def thank_you():
    return render_template('thank_you.html')

# Helper functions

def fetch_products_from_database():
    # Logic to retrieve products from the database
    # You can replace this with your own implementation
    products = [
        {'name': 'Product 1', 'description': 'This is product 1'},
        {'name': 'Product 2', 'description': 'This is product 2'},
        {'name': 'Product 3', 'description': 'This is product 3'}
    ]
    return products

def send_email(name, email, message):
    # Logic to send email
    # You can replace this with your own implementation
    print(f'Sending email to {email} from {name}: {message}')

# Run the application

if __name__ == '__main__':
    app.run(debug=True)
