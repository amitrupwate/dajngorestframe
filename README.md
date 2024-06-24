Vendor Management System
Overview
The Vendor Management System is a Django-based web application designed to handle vendor profiles, track purchase orders, and calculate vendor performance metrics. It leverages the Django REST Framework to provide RESTful API endpoints for managing vendors and purchase orders.

Features
Vendor Profile Management
Create, read, update, and delete vendor profiles.
Purchase Order Tracking
Track purchase orders with details like PO number, vendor reference, order date, items, quantity, and status.
Vendor Performance Evaluation
Calculate and retrieve performance metrics for vendors including on-time delivery rate, quality rating, average response time, and fulfillment rate.
Prerequisites
Python 3.7+
Django 3.2+
Django REST Framework
Installation
Clone the Repository

bash
Copy code
git clone https://github.com/amitrupwate/djangorestframework
cd djangorestframework
Create and Activate a Virtual Environment

bash
Copy code
python3 -m venv venv
source venv/bin/activate
Install Dependencies

bash
Copy code
pip install -r requirements.txt
Apply Migrations

bash
Copy code
python manage.py migrate
Create a Superuser

bash
Copy code
python manage.py createsuperuser
Run the Server

bash
Copy code
python manage.py runserver
API Endpoints
Vendor Management
Create a Vendor

URL: /api/vendors/
Method: POST
Request Body:
json
Copy code
{
    "name": "Vendor Name",
    "contact_details": "Contact Details",
    "address": "Vendor Address",
    "vendor_code": "Unique Vendor Code"
}
Response:
json
Copy code
{
    "id": 1,
    "name": "Vendor Name",
    "contact_details": "Contact Details",
    "address": "Vendor Address",
    "vendor_code": "Unique Vendor Code",
    "on_time_delivery_rate": 0.0,
    "quality_rating_avg": 0.0,
    "average_response_time": 0.0,
    "fulfillment_rate": 0.0
}
List All Vendors

URL: /api/vendors/
Method: GET
Response:
json
Copy code
[
    {
        "id": 1,
        "name": "Vendor Name",
        "contact_details": "Contact Details",
        "address": "Vendor Address",
        "vendor_code": "Unique Vendor Code",
        "on_time_delivery_rate": 0.0,
        "quality_rating_avg": 0.0,
        "average_response_time": 0.0,
        "fulfillment_rate": 0.0
    }
]
Retrieve a Specific Vendor

URL: /api/vendors/{vendor_id}/
Method: GET
Response:
json
Copy code
{
    "id": 1,
    "name": "Vendor Name",
    "contact_details": "Contact Details",
    "address": "Vendor Address",
    "vendor_code": "Unique Vendor Code",
    "on_time_delivery_rate": 0.0,
    "quality_rating_avg": 0.0,
    "average_response_time": 0.0,
    "fulfillment_rate": 0.0
}
Update a Vendor

URL: /api/vendors/{vendor_id}/
Method: PUT
Request Body:
json
Copy code
{
    "name": "Updated Vendor Name",
    "contact_details": "Updated Contact Details",
    "address": "Updated Vendor Address",
    "vendor_code": "Updated Unique Vendor Code"
}
Response:
json
Copy code
{
    "id": 1,
    "name": "Updated Vendor Name",
    "contact_details": "Updated Contact Details",
    "address": "Updated Vendor Address",
    "vendor_code": "Updated Unique Vendor Code",
    "on_time_delivery_rate": 0.0,
    "quality_rating_avg": 0.0,
    "average_response_time": 0.0,
    "fulfillment_rate": 0.0
}
Delete a Vendor

URL: /api/vendors/{vendor_id}/
Method: DELETE
Purchase Order Management
Create a Purchase Order

URL: /api/purchase_orders/
Method: POST
Request Body:
json
Copy code
{
    "id": 1,
        "po_number": "PO-2024002",
        "order_date": "2024-06-24T15:22:00Z",
        "delivery_date": "2024-07-24T15:23:00Z",
        "items": [
            {
                "name": "Laptops",
                "quantity": 10
            },
            {
                "name": "Monitors",
                "quantity": 5
            }
        ],
        "quantity": 15,
        "status": "pending",
        "quality_rating": 1.0,
        "issue_date": "2024-06-24T15:26:00Z",
        "acknowledgment_date": "2024-06-24T15:26:00Z",
        "vendor": 1
}
Response:
json
Copy code
{
    "id": 2,
        "po_number": "PO-2024003",
        "order_date": "2024-06-24T15:22:00Z",
        "delivery_date": "2024-07-24T15:23:00Z",
        "items": [
            {
                "name": "Laptops",
                "quantity": 10
            },
            {
                "name": "Monitors",
                "quantity": 5
            }
        ],
        "quantity": 15,
        "status": "pending",
        "quality_rating": 1.0,
        "issue_date": "2024-06-24T15:26:00Z",
        "acknowledgment_date": "2024-06-24T15:26:00Z",
        "vendor": 2
}
List All Purchase Orders

URL: /api/purchase_orders/
Method: GET
Response:
json
Copy code
[
    {
        "id": 3,
        "po_number": "PO-2024004",
        "order_date": "2024-06-24T15:22:00Z",
        "delivery_date": "2024-07-24T15:23:00Z",
        "items": [
            {
                "name": "Laptops",
                "quantity": 10
            },
            {
                "name": "Monitors",
                "quantity": 5
            }
        ],
        "quantity": 15,
        "status": "pending",
        "quality_rating": 1.0,
        "issue_date": "2024-06-24T15:26:00Z",
        "acknowledgment_date": "2024-06-24T15:26:00Z",
        "vendor": 3
    }
]
Retrieve a Specific Purchase Order

URL: /api/purchase_orders/{po_id}/
Method: GET
Response:
json
Copy code
{
    "id": 4,
        "po_number": "PO-2024005",
        "order_date": "2024-06-24T15:22:00Z",
        "delivery_date": "2024-07-24T15:23:00Z",
        "items": [
            {
                "name": "Laptops",
                "quantity": 10
            },
            {
                "name": "Monitors",
                "quantity": 5
            }
        ],
        "quantity": 15,
        "status": "pending",
        "quality_rating": 1.0,
        "issue_date": "2024-06-24T15:26:00Z",
        "acknowledgment_date": "2024-06-24T15:26:00Z",
        "vendor": 4
}
Update a Purchase Order

URL: /api/purchase_orders/{po_id}/
Method: PUT
Request Body:
json
Copy code
{
    "po_number": "PO123456",
    "vendor": 1,
    "order_date": "2024-06-24T00:00:00Z",
    "delivery_date": "2024-07-24T00:00:00Z",
    "items": [{"item": "Item 1", "quantity": 10}],
    "quantity": 10,
    "status": "completed",
    "quality_rating": 4.5,
    "issue_date": "2023-01-01T00:00:00Z",
    "acknowledgment_date": "2023-01-01T01:00:00Z"
}
Response:
json
Copy code
{
    "id": 5,
        "po_number": "PO-2024006",
        "order_date": "2024-06-24T15:22:00Z",
        "delivery_date": "2024-07-24T15:23:00Z",
        "items": [
            {
                "name": "Laptops",
                "quantity": 10
            },
            {
                "name": "Monitors",
                "quantity": 5
            }
        ],
        "quantity": 15,
        "status": "pending",
        "quality_rating": 1.0,
        "issue_date": "2024-06-24T15:26:00Z",
        "acknowledgment_date": "2024-06-24T15:26:00Z",
        "vendor": 5
