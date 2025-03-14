# Design Patterns

The system leverages Django’s Model-View-Template (MVT) pattern, enhancing maintainability and separation of concerns.

## Key Patterns Used
1. **Model-View-Template (MVT)**:
   - **Models**: Define the database schema and business logic.
   - **Views**: Handle HTTP requests and return responses.
   - **Templates**: Render HTML for the front-end.
2. **Class-Based Views (CBVs)**:
   - Reusable views for common tasks like listing, creating, and updating objects.
3. **Singleton Pattern**:
   - Used for managing database connections to ensure a single instance.

## Benefits
- Improved code maintainability.
- Faster development through reusable components.
- Clear separation of concerns.
