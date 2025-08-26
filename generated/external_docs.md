# Numbered Tabs

## Overview

The `bshowell0/numbered-tabs` repository is a backend service for a lightweight, demonstration-focused e-commerce and order management system. It is designed to be self-contained and easy to run, serving as a practical example of fundamental backend architecture.

## Core Concepts

The system is built around three main entities: **Users**, **Products**, and **Orders**.

{% cardGroup cols=3 gap="md" %}
{% card title="Users" icon="user" description="Manages user accounts and authentication." /%}
{% card title="Products" icon="package" description="Maintains the catalog of available products." /%}
{% card title="Orders" icon="shopping-cart" description="Handles order creation and processing." /%}
{% /cardGroup %}

{% callout type="info" %}
All data is managed in a non-persistent, in-memory database, which resets the application state upon each restart.
{% /callout %}

## Key Features

{% cardGroup cols=2 gap="md" %}
{% card title="User Management" description="Create, retrieve, and deactivate user accounts." icon="users" /%}
{% card title="Order Processing" description="Place new orders, list existing orders, and calculate order totals." icon="credit-card" /%}
{% card title="Product Catalog" description="Manage product information." icon="book-open" /%}
{% card title="Analytics Engine" description="Derive business insights, such as average order value, top-selling products, and user activity." icon="bar-chart-2" /%}
{% card title="API Layer" description="A RESTful API exposes all core functionalities for programmatic interaction." icon="server" /%}
{% /cardGroup %}

## Architecture

The codebase demonstrates a clear separation of concerns, with distinct layers for data storage, business logic, and API exposure.