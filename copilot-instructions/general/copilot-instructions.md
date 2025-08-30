# General Copilot Instructions

## Context

These instructions apply to all code generation tasks across the Logient-Nventive organization. They establish baseline standards for code quality, consistency, and maintainability.

### Activation Triggers

These instructions are active for all file types and project structures within the organization.

## Core Principles

### 1. Code Quality Standards

- Write clean, readable, and maintainable code
- Use meaningful variable and function names that clearly express intent
- Follow the single responsibility principle for functions and classes
- Prefer explicit code over clever code
- Include proper error handling for all operations that can fail

### 2. TypeScript First Approach

- Use TypeScript for all new JavaScript projects
- Prefer explicit type annotations over implicit types
- Use strict TypeScript configuration (`strict: true`)
- Avoid using `any` type unless absolutely necessary
- Define interfaces for all data structures

### 3. Documentation Standards

- Include JSDoc comments for all public functions and classes
- Write clear, concise inline comments for complex business logic
- Document function parameters, return values, and exceptions
- Keep documentation up-to-date with code changes

### 4. Testing Requirements

- Write unit tests for all new functionality
- Aim for meaningful test coverage (quality over quantity)
- Use descriptive test names that explain the behavior being tested
- Include both positive and negative test cases
- Mock external dependencies appropriately

## Coding Conventions

### Naming Conventions

- **Variables and Functions**: camelCase (e.g., `userName`, `calculateTotal`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_RETRY_ATTEMPTS`, `API_BASE_URL`)
- **Classes and Interfaces**: PascalCase (e.g., `UserService`, `IApiResponse`)
- **Files**: kebab-case for directories, PascalCase for components (e.g., `user-service/`, `UserProfile.tsx`)
- **Database**: snake_case for tables and columns (e.g., `user_profiles`, `created_at`)

### Code Organization

- Group related functionality into modules or services
- Use barrel exports (`index.ts`) for cleaner imports
- Organize files by feature rather than by file type
- Keep utility functions in dedicated utility modules
- Separate business logic from presentation logic

### Error Handling Patterns

```typescript
// Good: Explicit error handling with proper types
interface ApiError {
  message: string;
  code: string;
  statusCode: number;
}

async function fetchUserData(id: string): Promise<User> {
  try {
    const response = await api.get(`/users/${id}`);
    return response.data;
  } catch (error) {
    if (error instanceof ApiError) {
      logger.error(`Failed to fetch user ${id}:`, error);
      throw new UserNotFoundError(`User with ID ${id} not found`);
    }
    throw error;
  }
}
```

### Performance Considerations

- Use appropriate data structures for the task
- Implement proper caching strategies where applicable
- Avoid unnecessary re-computations
- Use lazy loading for large datasets
- Optimize database queries and API calls

## Security Guidelines

### Data Protection

- Validate and sanitize all user inputs
- Use parameterized queries to prevent SQL injection
- Implement proper authentication and authorization
- Never log sensitive information (passwords, tokens, PII)
- Use HTTPS for all network communications

### Secrets Management

- Never hardcode secrets, API keys, or credentials in source code
- Use environment variables or secure configuration management
- Rotate secrets regularly
- Use least-privilege access principles

## Framework-Specific Standards

### Frontend Development

- Use functional components with hooks in React
- Implement proper prop validation with TypeScript
- Handle loading and error states consistently
- Use CSS modules or styled-components for styling
- Implement proper accessibility features (ARIA labels, keyboard navigation)

### Backend Development

- Use dependency injection for better testability
- Implement proper request validation and sanitization
- Use structured logging with appropriate log levels
- Implement health checks and monitoring endpoints
- Follow RESTful API design principles

### Database Operations

- Use ORM/query builders rather than raw SQL when possible
- Implement proper database migrations
- Use database indexes appropriately
- Implement proper connection pooling
- Handle database transactions correctly

## Code Review Standards

### What to Look For

- Code follows established patterns and conventions
- Proper error handling is implemented
- Security considerations are addressed
- Tests are included and meaningful
- Documentation is complete and accurate

### Performance Reviews

- Check for potential performance bottlenecks
- Verify efficient algorithm and data structure usage
- Review database query efficiency
- Assess memory usage patterns

## Examples

### Good Function Example

```typescript
/**
 * Calculates the total price including tax for a list of items
 * @param items - Array of items with price and tax rate
 * @param discountPercentage - Optional discount to apply (0-100)
 * @returns Total price including tax and discount
 * @throws {ValidationError} When items array is empty or discount is invalid
 */
async function calculateTotalPrice(
  items: PriceItem[],
  discountPercentage = 0
): Promise<number> {
  if (!items.length) {
    throw new ValidationError("Items array cannot be empty");
  }

  if (discountPercentage < 0 || discountPercentage > 100) {
    throw new ValidationError("Discount must be between 0 and 100");
  }

  const subtotal = items.reduce((total, item) => {
    return total + item.price * (1 + item.taxRate);
  }, 0);

  const discountAmount = subtotal * (discountPercentage / 100);
  return Math.round((subtotal - discountAmount) * 100) / 100;
}
```

### Good Error Handling Example

```typescript
class UserService {
  async createUser(userData: CreateUserRequest): Promise<User> {
    try {
      // Validate input
      const validationResult = await this.validateUserData(userData);
      if (!validationResult.isValid) {
        throw new ValidationError(validationResult.errors);
      }

      // Check for existing user
      const existingUser = await this.findUserByEmail(userData.email);
      if (existingUser) {
        throw new ConflictError("User with this email already exists");
      }

      // Create user
      const hashedPassword = await this.hashPassword(userData.password);
      const user = await this.userRepository.create({
        ...userData,
        password: hashedPassword,
      });

      this.logger.info(`User created successfully: ${user.id}`);
      return user;
    } catch (error) {
      this.logger.error("Failed to create user:", error);

      if (error instanceof ValidationError || error instanceof ConflictError) {
        throw error; // Re-throw business logic errors
      }

      // Convert unexpected errors to generic error
      throw new InternalServerError("Failed to create user");
    }
  }
}
```

## Version History

- **v1.0** (2025-08-30): Initial creation
  - Basic coding standards and conventions
  - Error handling patterns
  - Security guidelines
  - Documentation requirements

---

**Last Updated**: August 30, 2025  
**Maintained by**: DevOps Team, Technical Leads
