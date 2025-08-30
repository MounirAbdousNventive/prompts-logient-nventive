# TypeScript Style Guide

## 🎯 Overview

This document defines the coding standards and style guidelines for TypeScript development at Logient/Nventive.

## 📋 Basic Formatting

### Indentation

- Use 2 spaces for indentation (no tabs)
- Consistent indentation throughout the codebase

### Line Length

- Maximum line length: 100 characters
- Break long lines at logical points

### Semicolons

- Always use semicolons to terminate statements
- Consistent with TypeScript compiler expectations

```typescript
// ✅ Good
const message = "Hello, world!";
const result = calculateSum(a, b);

// ❌ Bad
const message = "Hello, world!";
const result = calculateSum(a, b);
```

## 🏷️ Naming Conventions

### Variables and Functions

- Use camelCase for variables and functions
- Use descriptive names that clearly indicate purpose

```typescript
// ✅ Good
const userAge = 25;
const calculateTotalPrice = (items: Item[]) => {
  /* */
};

// ❌ Bad
const ua = 25;
const calc = (items: Item[]) => {
  /* */
};
```

### Classes and Interfaces

- Use PascalCase for classes and interfaces
- Prefix interfaces with 'I' when needed for disambiguation

```typescript
// ✅ Good
class UserManager {}
interface IUserRepository {}
interface UserPreferences {}

// ❌ Bad
class userManager {}
interface userRepository {}
```

### Constants

- Use SCREAMING_SNAKE_CASE for module-level constants
- Use camelCase for local constants

```typescript
// ✅ Good
const API_BASE_URL = "https://api.example.com";
const DEFAULT_TIMEOUT = 5000;

function processData() {
  const maxRetries = 3; // local constant
}
```

## 🏗️ Type Definitions

### Explicit Types

- Always define explicit return types for functions
- Use type annotations for complex variables

```typescript
// ✅ Good
function getUserById(id: string): Promise<User | null> {
  return userRepository.findById(id);
}

const users: User[] = [];

// ❌ Bad
function getUserById(id: string) {
  return userRepository.findById(id);
}

const users = [];
```

### Interface vs Type

- Use `interface` for object shapes that might be extended
- Use `type` for unions, intersections, and computed types

```typescript
// ✅ Good
interface User {
  id: string;
  name: string;
}

interface AdminUser extends User {
  permissions: string[];
}

type Status = "pending" | "approved" | "rejected";
type UserWithStatus = User & { status: Status };
```

## 📦 Imports and Exports

### Import Organization

1. Node.js built-in modules
2. Third-party libraries
3. Internal modules (absolute paths)
4. Relative imports

```typescript
// ✅ Good
import { readFile } from "fs/promises";
import express from "express";
import { Logger } from "@/utils/Logger";
import { UserService } from "../services/UserService";
```

### Export Patterns

- Use named exports by default
- Use default exports sparingly, only for main module exports

```typescript
// ✅ Good
export class UserService {}
export const DEFAULT_CONFIG = {};

// ✅ Acceptable for main module export
export default class Application {}
```

## 🛡️ Error Handling

### Type-Safe Error Handling

- Use Result types or explicit error handling
- Avoid throwing errors in pure functions

```typescript
// ✅ Good
type Result<T, E = Error> =
  | { success: true; data: T }
  | { success: false; error: E };

async function fetchUser(id: string): Promise<Result<User>> {
  try {
    const user = await userRepository.findById(id);
    return { success: true, data: user };
  } catch (error) {
    return { success: false, error: error as Error };
  }
}
```

## 📝 Documentation

### TSDoc Comments

- Use TSDoc for all public APIs
- Include parameter descriptions and return value documentation

```typescript
/**
 * Calculates the total price including tax
 * @param basePrice - The base price before tax
 * @param taxRate - The tax rate as a decimal (e.g., 0.1 for 10%)
 * @returns The total price including tax
 */
function calculateTotalPrice(basePrice: number, taxRate: number): number {
  return basePrice * (1 + taxRate);
}
```

## 🔧 Configuration

### ESLint Rules

Recommended ESLint configuration additions:

```json
{
  "@typescript-eslint/explicit-function-return-type": "error",
  "@typescript-eslint/no-explicit-any": "error",
  "@typescript-eslint/no-unused-vars": "error",
  "@typescript-eslint/prefer-const": "error"
}
```

### Prettier Configuration

```json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 100,
  "tabWidth": 2
}
```
