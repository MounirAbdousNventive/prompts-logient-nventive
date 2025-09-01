# API Reference

> Complete reference for the Prompts Sync Extension commands, configuration options, and programmatic interfaces.

## 🎯 Overview

This document provides comprehensive reference information for developers and administrators working with the Logient-Nventive Shared Prompt Bank system, including VS Code extension APIs, configuration schemas, and command interfaces.

## 📋 Extension Commands

### User Commands

Commands available through the VS Code Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`):

#### `promptsSync.syncNow`

**Title**: "Prompts Sync: Sync Now"  
**Description**: Manually trigger an immediate synchronization with the remote repository

```typescript
interface SyncNowCommand {
  command: "promptsSync.syncNow";
  title: "Sync Now";
  category: "Prompts Sync";
}
```

**Usage**:

- Available at any time when the extension is active
- Forces sync regardless of current schedule settings
- Shows progress notification during execution
- Displays result notification on completion

**Return Value**: `Promise<void>`

**Errors**:

- `AuthenticationError`: GitHub authentication failed
- `NetworkError`: Unable to connect to repository
- `FileSystemError`: Cannot write to prompts directory
- `ConfigurationError`: Invalid extension settings

#### `promptsSync.showStatus`

**Title**: "Prompts Sync: Show Status"  
**Description**: Display detailed information about sync status and history

```typescript
interface ShowStatusCommand {
  command: "promptsSync.showStatus";
  title: "Show Status";
  category: "Prompts Sync";
}
```

**Usage**:

- Shows current configuration settings
- Displays last sync time and result
- Lists any errors or warnings
- Provides diagnostic information

**Return Value**: `Promise<void>`

### Internal Commands

Commands used internally by the extension:

#### `promptsSync.openSettings`

**Description**: Open extension settings in VS Code preferences

#### `promptsSync.resetConfiguration`

**Description**: Reset all extension settings to defaults

#### `promptsSync.viewLogs`

**Description**: Open the extension log output channel

## ⚙️ Configuration Schema

### Complete Configuration Object

```typescript
interface PromptsyncConfiguration {
  enabled: boolean;
  frequency: SyncFrequency;
  customPath: string;
  repository: string;
  branch: string;
  syncOnStartup: boolean;
  showNotifications: boolean;
  debug: boolean;
}
```

### Individual Configuration Properties

#### `promptsSync.enabled`

**Type**: `boolean`  
**Default**: `true`  
**Description**: Enable or disable automatic prompts synchronization

```json
{
  "promptsSync.enabled": true
}
```

**Behavior**:

- When `false`: No automatic syncing occurs, manual sync is still available
- When `true`: Syncing occurs according to frequency setting
- Changes take effect immediately without restart

#### `promptsSync.frequency`

**Type**: `string`  
**Default**: `"daily"`  
**Options**: `"startup" | "hourly" | "daily" | "weekly" | "manual"`

```json
{
  "promptsSync.frequency": "daily"
}
```

**Sync Schedules**:

- `"startup"`: Sync only when VS Code starts (if `syncOnStartup` is true)
- `"hourly"`: Sync every 60 minutes while VS Code is running
- `"daily"`: Sync once every 24 hours from last sync
- `"weekly"`: Sync once every 7 days from last sync
- `"manual"`: Only sync when manually triggered

#### `promptsSync.customPath`

**Type**: `string`  
**Default**: `""`  
**Description**: Custom directory path for storing prompts

```json
{
  "promptsSync.customPath": "/Users/username/custom-prompts"
}
```

**Behavior**:

- Empty string uses OS-specific default path
- Must be an absolute path if specified
- Directory will be created if it doesn't exist
- Must have write permissions

**Default Paths by OS**:

- **macOS**: `~/Library/Application Support/Code/User/prompts`
- **Windows**: `%APPDATA%\Code\User\prompts`
- **Linux**: `~/.config/Code/User/prompts`

#### `promptsSync.repository`

**Type**: `string`  
**Default**: `"https://github.com/MounirAbdousNventive/prompts-logient-nventive"`  
**Description**: Git repository URL to sync prompts from

```json
{
  "promptsSync.repository": "https://github.com/YourOrg/your-prompts-repo"
}
```

**Supported Formats**:

- HTTPS: `https://github.com/owner/repo`
- SSH: `git@github.com:owner/repo.git`
- GitHub Enterprise: `https://github.enterprise.com/owner/repo`

#### `promptsSync.branch`

**Type**: `string`  
**Default**: `"master"`  
**Description**: Repository branch to sync from

```json
{
  "promptsSync.branch": "main"
}
```

#### `promptsSync.syncOnStartup`

**Type**: `boolean`  
**Default**: `true`  
**Description**: Whether to sync when VS Code starts

```json
{
  "promptsSync.syncOnStartup": false
}
```

#### `promptsSync.showNotifications`

**Type**: `boolean`  
**Default**: `true`  
**Description**: Show notifications for sync operations

```json
{
  "promptsSync.showNotifications": false
}
```

**Notification Types**:

- Sync start (if enabled and taking >2 seconds)
- Sync completion with summary
- Sync errors with actionable guidance
- Configuration changes requiring restart

#### `promptsSync.debug`

**Type**: `boolean`  
**Default**: `false`  
**Description**: Enable detailed debug logging

```json
{
  "promptsSync.debug": true
}
```

**Debug Information Includes**:

- Detailed sync operation logs
- File system operation details
- GitHub API request/response information
- Performance timing information

## 🔧 Programmatic APIs

### Extension Activation API

```typescript
interface PromptsyncExtension {
  activate(context: vscode.ExtensionContext): void;
  deactivate(): void;
}
```

### Sync Manager API

```typescript
interface SyncManager {
  initialize(context: vscode.ExtensionContext): Promise<void>;
  syncNow(): Promise<SyncResult>;
  getStatus(): SyncStatus;
  dispose(): void;
}

interface SyncResult {
  success: boolean;
  filesUpdated: number;
  filesDeleted: number;
  errors: SyncError[];
  duration: number;
  timestamp: Date;
}

interface SyncStatus {
  lastSync: Date | null;
  nextScheduledSync: Date | null;
  isEnabled: boolean;
  currentFrequency: SyncFrequency;
  repositoryUrl: string;
  localPath: string;
  errors: SyncError[];
}

interface SyncError {
  code: string;
  message: string;
  details?: any;
  timestamp: Date;
}
```

### Configuration Manager API

```typescript
interface ConfigManager {
  getConfiguration(): PromptsyncConfiguration;
  updateConfiguration(partial: Partial<PromptsyncConfiguration>): Promise<void>;
  validateConfiguration(config: PromptsyncConfiguration): ValidationResult;
  onConfigurationChanged(
    callback: (change: ConfigurationChange) => void
  ): vscode.Disposable;
}

interface ValidationResult {
  isValid: boolean;
  errors: string[];
  warnings: string[];
}

interface ConfigurationChange {
  key: string;
  oldValue: any;
  newValue: any;
}
```

### Status Bar Manager API

```typescript
interface StatusBarManager {
  updateStatus(status: SyncStatus): void;
  showProgress(message: string): void;
  hideProgress(): void;
  dispose(): void;
}
```

## 📊 Event System

### Event Types

The extension emits various events that can be monitored:

```typescript
interface SyncEvents {
  onSyncStarted: (context: SyncContext) => void;
  onSyncProgress: (progress: SyncProgress) => void;
  onSyncCompleted: (result: SyncResult) => void;
  onSyncError: (error: SyncError) => void;
  onConfigurationChanged: (change: ConfigurationChange) => void;
}

interface SyncContext {
  triggeredBy: "manual" | "scheduled" | "startup";
  repository: string;
  branch: string;
  localPath: string;
}

interface SyncProgress {
  phase: "authentication" | "fetching" | "comparing" | "updating" | "cleanup";
  message: string;
  percentage?: number;
}
```

### Event Registration

```typescript
// Register for sync events
const disposable = vscode.extensions
  .getExtension("logient-nventive.prompts-sync-extension")
  ?.exports?.onSyncCompleted((result: SyncResult) => {
    console.log(`Sync completed: ${result.filesUpdated} files updated`);
  });

// Remember to dispose when no longer needed
disposable?.dispose();
```

## 🌐 Network and Authentication

### GitHub Authentication

The extension uses VS Code's built-in GitHub authentication:

```typescript
interface GitHubAuth {
  getSession(): Promise<vscode.AuthenticationSession | undefined>;
  createSession(): Promise<vscode.AuthenticationSession>;
  removeSession(): Promise<void>;
}
```

**Authentication Scopes**:

- `repo`: For accessing private repositories
- `public_repo`: For accessing public repositories
- `read:user`: For user identification

### Network Configuration

```typescript
interface NetworkConfig {
  timeout: number; // Request timeout in milliseconds
  retryCount: number; // Number of retry attempts
  retryDelay: number; // Delay between retries in milliseconds
}

// Default network configuration
const defaultNetworkConfig: NetworkConfig = {
  timeout: 30000, // 30 seconds
  retryCount: 3, // 3 retry attempts
  retryDelay: 1000, // 1 second delay
};
```

## 📁 File System Operations

### File System API

```typescript
interface FileSystemOperations {
  ensureDirectory(path: string): Promise<void>;
  copyFile(source: string, destination: string): Promise<void>;
  deleteFile(path: string): Promise<void>;
  listFiles(directory: string, pattern?: string): Promise<string[]>;
  getFileStats(path: string): Promise<FileStats>;
  createBackup(filePath: string): Promise<string>;
  restoreBackup(backupPath: string, originalPath: string): Promise<void>;
}

interface FileStats {
  size: number;
  created: Date;
  modified: Date;
  isDirectory: boolean;
  permissions: FilePermissions;
}

interface FilePermissions {
  readable: boolean;
  writable: boolean;
  executable: boolean;
}
```

### Path Resolution

```typescript
interface PathResolver {
  getDefaultPromptsPath(): string;
  resolveCustomPath(customPath: string): string;
  validatePath(path: string): PathValidationResult;
}

interface PathValidationResult {
  isValid: boolean;
  isAbsolute: boolean;
  exists: boolean;
  isWritable: boolean;
  errors: string[];
}
```

## 🚨 Error Handling

### Error Types

```typescript
enum SyncErrorCode {
  // Authentication errors
  AUTHENTICATION_FAILED = "AUTH_FAILED",
  AUTHENTICATION_EXPIRED = "AUTH_EXPIRED",
  REPOSITORY_ACCESS_DENIED = "REPO_ACCESS_DENIED",

  // Network errors
  NETWORK_ERROR = "NETWORK_ERROR",
  REPOSITORY_NOT_FOUND = "REPO_NOT_FOUND",
  CONNECTION_TIMEOUT = "CONNECTION_TIMEOUT",

  // File system errors
  FILE_SYSTEM_ERROR = "FS_ERROR",
  PERMISSION_DENIED = "PERMISSION_DENIED",
  DISK_FULL = "DISK_FULL",
  PATH_NOT_FOUND = "PATH_NOT_FOUND",

  // Configuration errors
  CONFIGURATION_ERROR = "CONFIG_ERROR",
  INVALID_REPOSITORY_URL = "INVALID_REPO_URL",
  INVALID_BRANCH = "INVALID_BRANCH",

  // Content errors
  INVALID_PROMPT_FORMAT = "INVALID_PROMPT_FORMAT",
  CORRUPTED_FILE = "CORRUPTED_FILE",
}

class SyncError extends Error {
  constructor(
    message: string,
    public readonly code: SyncErrorCode,
    public readonly details?: any,
    public readonly cause?: Error
  ) {
    super(message);
    this.name = "SyncError";
  }
}
```

### Error Recovery

```typescript
interface ErrorRecovery {
  canRecover(error: SyncError): boolean;
  suggestedAction(error: SyncError): RecoveryAction;
  performRecovery(error: SyncError): Promise<RecoveryResult>;
}

interface RecoveryAction {
  type: "retry" | "reconfigure" | "manual" | "ignore";
  message: string;
  autoExecute: boolean;
}

interface RecoveryResult {
  success: boolean;
  message: string;
  requiresUserAction: boolean;
}
```

## 📋 Logging and Monitoring

### Logging API

```typescript
interface Logger {
  debug(message: string, data?: any): void;
  info(message: string, data?: any): void;
  warn(message: string, data?: any): void;
  error(message: string, error?: Error): void;

  // Structured logging
  logSyncOperation(operation: SyncOperation): void;
  logPerformanceMetric(metric: PerformanceMetric): void;
  logUserAction(action: UserAction): void;
}

interface SyncOperation {
  type: "start" | "progress" | "complete" | "error";
  phase?: string;
  repository: string;
  branch: string;
  filesAffected?: number;
  duration?: number;
  error?: SyncError;
}

interface PerformanceMetric {
  operation: string;
  duration: number;
  memoryUsage?: number;
  networkBytes?: number;
}

interface UserAction {
  command: string;
  triggeredBy: "menu" | "command-palette" | "shortcut" | "api";
  timestamp: Date;
}
```

### Monitoring Metrics

```typescript
interface SyncMetrics {
  totalSyncs: number;
  successfulSyncs: number;
  failedSyncs: number;
  averageSyncDuration: number;
  lastSyncTime: Date | null;
  totalFilesSync: number;
  totalBytesSynced: number;
  errorsByType: Record<SyncErrorCode, number>;
}

interface UsageMetrics {
  extensionActivations: number;
  manualSyncsTriggered: number;
  configurationChanges: number;
  userCommandExecutions: Record<string, number>;
}
```

## 🔌 Extension Integration

### VS Code Extension API Usage

```typescript
// Extension manifest contribution points
interface ExtensionContributions {
  configuration: ConfigurationContribution;
  commands: CommandContribution[];
  menus: MenuContribution[];
  statusBar: StatusBarContribution;
}

interface ConfigurationContribution {
  title: string;
  properties: Record<string, ConfigurationProperty>;
}

interface ConfigurationProperty {
  type: "boolean" | "string" | "number" | "array" | "object";
  default: any;
  description: string;
  enum?: string[];
  minimum?: number;
  maximum?: number;
}

interface CommandContribution {
  command: string;
  title: string;
  category?: string;
  when?: string;
  icon?: string;
}
```

### Extension Dependencies

```typescript
interface ExtensionDependencies {
  // VS Code API version requirement
  engines: {
    vscode: string; // "^1.70.0"
  };

  // Optional extension dependencies
  extensionDependencies?: string[];

  // Runtime dependencies
  dependencies: Record<string, string>;

  // Development dependencies
  devDependencies: Record<string, string>;
}
```

## 📚 Type Definitions

### Complete Type Reference

```typescript
// Re-export all types for external consumption
export {
  PromptsyncConfiguration,
  SyncManager,
  ConfigManager,
  StatusBarManager,
  SyncResult,
  SyncStatus,
  SyncError,
  SyncErrorCode,
  SyncFrequency,
  FileSystemOperations,
  Logger,
  NetworkConfig,
  PathResolver,
};

// Utility types
export type SyncFrequency =
  | "startup"
  | "hourly"
  | "daily"
  | "weekly"
  | "manual";

export type ConfigurationKey = keyof PromptsyncConfiguration;

export type SyncPhase =
  | "authentication"
  | "fetching"
  | "comparing"
  | "updating"
  | "cleanup";

export type NotificationType = "info" | "warning" | "error" | "progress";
```

## 🔗 Related APIs

### GitHub API Integration

The extension interfaces with GitHub's REST API v4:

**Endpoints Used**:

- `GET /repos/{owner}/{repo}` - Repository information
- `GET /repos/{owner}/{repo}/contents/{path}` - File contents
- `GET /repos/{owner}/{repo}/commits` - Commit history
- `GET /user` - User authentication verification

**Rate Limiting**:

- Authenticated requests: 5,000 per hour
- The extension implements automatic rate limiting and retry logic

### VS Code Settings Sync

The extension integrates with VS Code's settings sync:

```typescript
interface SettingsSyncIntegration {
  isSyncEnabled(): boolean;
  shouldSyncConfiguration(): boolean;
  onSettingsSync(callback: () => void): vscode.Disposable;
}
```

## 📞 Support and Troubleshooting

### Diagnostic Commands

```typescript
// Generate diagnostic report
interface DiagnosticReport {
  extensionVersion: string;
  vscodeVersion: string;
  operatingSystem: string;
  configuration: PromptsyncConfiguration;
  lastSyncResult: SyncResult | null;
  recentErrors: SyncError[];
  environmentInfo: EnvironmentInfo;
}

interface EnvironmentInfo {
  nodeVersion: string;
  gitVersion: string;
  networkAccess: boolean;
  fileSystemPermissions: boolean;
}
```

For additional support:

- [Installation Guide](installation-guide.md)
- [Usage Guide](usage-guide.md)
- [Troubleshooting Section](installation-guide.md#-troubleshooting-installation)
- [GitHub Issues](https://github.com/MounirAbdousNventive/prompts-logient-nventive/issues)

---

**This API reference is maintained alongside the extension code. For the most up-to-date information, consult the TypeScript definitions in the source code.**
