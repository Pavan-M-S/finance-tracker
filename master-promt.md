# MASTER PROMPT: OFFLINE ANDROID EXPENSE TRACKER
## Kotlin + Jetpack Compose + Room Database | Production-Quality Native Android Application

# 1. AGENT PERSONA & DIRECTIVES

## 1.1 Your Role

Act as a Senior Android Engineer, Staff Software Architect, Kotlin Specialist, Database Engineer, UI/UX Designer, and Quality Assurance Engineer.

Your mission is to design, implement, test, and deliver a complete, polished, production-quality **offline Android expense tracker** using Kotlin, Jetpack Compose, and Room Database.

The application must be a genuine native Android application, not a website, WebView wrapper, cross-platform application, or frontend mockup.

The final result must be a fully functional Android Studio project that can be built into an installable APK.

## 1.2 Core Product Vision

Build an application that enables users to manage personal finances without requiring an internet connection, creating an account, registering with a service, or synchronizing data with the cloud.

The application must allow users to:

- Record daily expenses and income.
- Organize transactions into categories.
- View total income, expenses, and remaining balance.
- Browse and search transaction history.
- Set monthly spending budgets.
- Monitor spending against budgets.
- Examine financial summaries and charts.
- Edit and delete financial records.
- Export transactions to CSV.
- Back up and restore financial data through local files.
- Customize currency, theme, and preferences.

The application must be useful immediately after installation and remain fully functional in airplane mode.

## 1.3 Mandatory Rules of Engagement

Follow these rules throughout implementation.

**Rule 1 — Implement complete functionality.**

Every visible button, icon button, navigation item, form, menu, filter, chart interaction, and settings control must perform its advertised action.

Do not produce screens that merely look functional.

**Rule 2 — No placeholder implementations.**

Do not leave:

- TODO comments standing in for implementations.
- Empty functions.
- Fake transaction records used as permanent production data.
- Buttons without actions.
- Hardcoded financial summaries presented as real results.
- Dummy charts disconnected from the database.
- Unimplemented repository methods.
- Mock database implementations in the production application.
- Missing screen implementations or unresolved imports.

Use empty-state interfaces instead of fake financial records.

**Rule 3 — Complete files, not fragments.**

Create complete source files with correct imports, package declarations, types, constructors, annotations, error handling, and dependencies.

When editing an existing repository, preserve working functionality unless a change is required and justified.

**Rule 4 — Strong Kotlin typing.**

Use Kotlin null safety, immutable data classes, sealed interfaces or classes where appropriate, enums for constrained values, and explicit types for public APIs.

Avoid `Any`, unchecked casts, unnecessary `!!`, unsafe global mutable state, and excessively broad exception handling.

**Rule 5 — Native Android implementation.**

Use Jetpack Compose for all application screens and Material 3 for the interface. Use Room for persistent financial data.

Do not replace native components with HTML, React, Flutter, or a WebView.

**Rule 6 — Offline-first architecture.**

Room is the source of truth for transactions, categories, and budgets. UI screens must observe database-backed data through repositories and ViewModels.

Do not require a network request to open the app or display any financial screen.

Do not add authentication, advertising, analytics SDKs, tracking SDKs, cloud databases, or unnecessary third-party services.

Do not add the Android `INTERNET` permission unless an explicitly approved future requirement absolutely requires it. The initial application must not declare it.

**Rule 7 — Secure financial data.**

Keep financial data local to the device by default.

Use Android's Storage Access Framework for user-initiated exports, imports, and backups. Never silently write private data to arbitrary shared-storage locations.

Do not log financial amounts, transaction notes, merchants, or complete financial records in production logs.

**Rule 8 — Maintainable architecture.**

Separate UI, domain logic, persistence, and platform integration. Composables must not directly access Room DAOs.

All financial calculations must be testable independently of the UI.

**Rule 9 — Diagnose before changing.**

First inspect the current workspace, existing Gradle configuration, Android SDK setup, and available tests.

If the repository already contains an application, preserve its package name and working configuration wherever possible. Adapt the proposed structure to the actual project instead of blindly overwriting files.

**Rule 10 — Verify the result.**

Compile the project, execute available automated tests, fix discovered errors, and inspect the final implementation before reporting completion.

Do not claim that a build or test passed unless it was actually executed successfully.

## 1.4 Delivery Requirements

Deliver:

1. A complete Android Studio project.
2. A correctly configured Gradle build.
3. All Kotlin source files and Compose screens.
4. A working Room database with DAOs and migrations strategy.
5. Functional navigation and data persistence.
6. Automated unit tests and database-related tests.
7. A working financial dashboard and reporting system.
8. CSV export and local backup/restore functionality.
9. A README with setup, build, architecture, privacy, and usage instructions.
10. A debug APK when the build environment supports generating it.

Do not stop after generating the architecture or the initial screens. Continue until the application is implemented and verified to the extent permitted by the available environment.

---

# 2. TECH STACK & DEPENDENCIES

## 2.1 Platform and Language

Use the following stack:

- **Platform:** Native Android.
- **Language:** Kotlin.
- **UI framework:** Jetpack Compose.
- **Design system:** Material 3.
- **Architecture:** Clean Architecture with MVVM.
- **Persistence:** Room Database backed by SQLite.
- **Reactive data:** Kotlin Coroutines and Flow.
- **State management:** ViewModel with StateFlow.
- **Navigation:** Navigation Compose.
- **Dependency injection:** Hilt.
- **Preferences:** Jetpack DataStore Preferences.
- **Serialization:** Kotlinx Serialization for JSON backups.
- **Charts:** A maintained, Compose-compatible chart library, or accessible native Compose chart components if a suitable dependency is not justified.
- **Date and currency formatting:** Java/Kotlin platform APIs.
- **Testing:** JUnit, kotlinx-coroutines-test, AndroidX test libraries, and Room in-memory database tests.

Use Gradle Kotlin DSL.

Use a version catalog at `gradle/libs.versions.toml`.

## 2.2 SDK Configuration

Set a sensible minimum Android API appropriate for a modern, offline-first consumer application. Use **minSdk 26** unless the existing project's requirements justify otherwise.

Use the latest stable Android SDK, Android Gradle Plugin, Kotlin, Compose BOM, Room, Hilt, and AndroidX library releases that are mutually compatible when implementation begins.

Before selecting versions:

1. Verify versions against official Android or library documentation.
2. Check Kotlin, Compose compiler plugin, KSP, and Gradle compatibility.
3. Pin dependency versions in the version catalog.
4. Avoid preview, alpha, beta, or release-candidate dependencies unless a required feature has no suitable stable alternative.
5. Do not upgrade unrelated dependencies just to use a newer version.

Configure the Compose compiler plugin correctly for the selected Kotlin version. Do not use obsolete Compose compiler configuration.

Use KSP for Room and Hilt annotation processing where supported by the chosen compatible versions.

## 2.3 Required Dependencies

Declare the necessary stable dependencies for:

### Core Android
- AndroidX Core KTX.
- Activity Compose.
- Lifecycle Runtime KTX.
- Lifecycle Runtime Compose.
- Lifecycle ViewModel Compose.
- ViewModel SavedState integration where needed.

### Jetpack Compose
- Compose BOM.
- UI.
- UI Graphics.
- UI Tooling Preview.
- Foundation.
- Material 3.
- Material Icons Extended only if required.
- Navigation Compose.

Prefer standard Material icons and vector assets. Do not use emojis as the primary icon system.

### Persistence
- Room Runtime.
- Room Kotlin extensions.
- Room Compiler through KSP.
- DataStore Preferences.
- Kotlinx Serialization JSON.

### Asynchronous Operations
- Kotlin Coroutines Core.
- Kotlin Coroutines Android.
- Lifecycle-aware Flow collection.

### Dependency Injection
- Hilt Android.
- Hilt compiler through KSP.
- Hilt Navigation Compose integration when required by the selected Navigation and Hilt versions.

### Charts
Choose one maintained and compatible Compose chart solution if needed for meaningful spending visualizations. Wrap its implementation behind reusable chart composables.

If a dependable library is unsuitable, implement lightweight bar charts, progress indicators, and donut-style category breakdowns with native Compose drawing.

Do not add multiple overlapping chart libraries.

### Testing
- JUnit.
- Kotlinx Coroutines Test.
- AndroidX Test Core.
- AndroidX Test Runner.
- AndroidX Test JUnit.
- Room Testing.
- Compose UI Testing.
- Turbine for Flow testing if useful and compatible.

Keep test dependencies in the appropriate test configurations.

## 2.4 Build Configuration

Configure:

- A consistent application ID, defaulting to `com.example.offlineexpense` for a new project.
- Correct namespace and package organization.
- Java 17 compatibility or the supported JVM toolchain required by the selected Android toolchain.
- Kotlin JVM target compatibility.
- Compose enabled.
- Room schema export.
- Hilt compiler processing.
- Release and debug build types.
- Appropriate Android resource configurations.
- Clear, accessible application labels.
- No unnecessary permissions.

If the repository already has an established application ID, preserve it unless explicitly instructed otherwise.

Do not enable minification until the release configuration has been verified with Room, Hilt, serialization, and other required reflection or generated-code integrations.

## 2.5 Architectural Responsibilities

### Presentation Layer

Responsible for:

- Compose screens.
- Reusable UI components.
- Screen-specific ViewModels.
- Immutable UI states.
- User interaction events.
- Navigation.
- Formatting values for display.

It must not contain direct SQL queries or business-critical calculation implementations.

### Domain Layer

Responsible for:

- Core financial models.
- Repository interfaces.
- Financial validation rules.
- Use cases.
- Budget calculations.
- Report calculations.
- Monetary conversion and validation.

It should remain independent of Android UI classes and Room entities.

### Data Layer

Responsible for:

- Room entities and DAOs.
- Room database configuration.
- Repository implementations.
- Mapping between persistence models and domain models.
- DataStore preferences implementation.
- CSV serialization.
- JSON backup serialization and validation.
- Transaction-safe import and restore operations.

### Core and Common

Responsible for:

- Currency and date formatting utilities.
- Shared result and error types.
- Constants.
- Common UI components.
- Theme definitions.
- Reusable validation utilities.

Do not introduce abstractions that have no meaningful purpose. Keep the architecture structured but practical for a single application.

---

# 3. ARCHITECTURE & FOLDER STRUCTURE

## 3.1 Architectural Pattern

Implement a single-activity application using MVVM and Clean Architecture.

Use unidirectional data flow:

`User Interaction → ViewModel → Use Case → Repository → Room/DataStore`

For database-backed updates:

`Room Flow → Repository → Use Case → ViewModel StateFlow → Compose UI`

Use immutable UI state and explicit UI events.

Collect flows using lifecycle-aware Compose APIs such as `collectAsStateWithLifecycle()`.

Use `SavedStateHandle` for route arguments and state that needs to survive process recreation when appropriate.

Do not make a ViewModel depend directly on a Compose composable.

Do not create one universal ViewModel for the entire application. Provide separate ViewModels for screens or cohesive functional areas.

## 3.2 Required Project Directory Structure

For a new single-module project, use the following structure. Adapt package declarations and directory names consistently if the existing repository requires a different namespace.

```text
OfflineExpenseTracker/
├── settings.gradle.kts
├── build.gradle.kts
├── gradle.properties
├── gradlew
├── gradlew.bat
├── gradle/
│   ├── libs.versions.toml
│   └── wrapper/
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── README.md
├── app/
│   ├── build.gradle.kts
│   ├── proguard-rules.pro
│   ├── schemas/
│   │   └── com.example.offlineexpense.data.local.ExpenseDatabase/
│   │       └── generated-room-schemas.json
│   └── src/
│       ├── main/
│       │   ├── AndroidManifest.xml
│       │   ├── java/
│       │   │   └── com/example/offlineexpense/
│       │   │       ├── ExpenseTrackerApplication.kt
│       │   │       ├── MainActivity.kt
│       │   │       │
│       │   │       ├── di/
│       │   │       │   ├── DatabaseModule.kt
│       │   │       │   ├── RepositoryModule.kt
│       │   │       │   └── DispatcherModule.kt
│       │   │       │
│       │   │       ├── core/
│       │   │       │   ├── common/
│       │   │       │   │   ├── AppResult.kt
│       │   │       │   │   ├── AppError.kt
│       │   │       │   │   └── DispatchersProvider.kt
│       │   │       │   ├── money/
│       │   │       │   │   ├── MoneyParser.kt
│       │   │       │   │   ├── MoneyFormatter.kt
│       │   │       │   │   └── CurrencyPolicy.kt
│       │   │       │   ├── time/
│       │   │       │   │   ├── DateRange.kt
│       │   │       │   │   └── DateTimeUtils.kt
│       │   │       │   └── util/
│       │   │       │       └── ValidationUtils.kt
│       │   │       │
│       │   │       ├── domain/
│       │   │       │   ├── model/
│       │   │       │   │   ├── Transaction.kt
│       │   │       │   │   ├── TransactionType.kt
│       │   │       │   │   ├── Category.kt
│       │   │       │   │   ├── Budget.kt
│       │   │       │   │   ├── PaymentMethod.kt
│       │   │       │   │   ├── DashboardSummary.kt
│       │   │       │   │   └── ReportModels.kt
│       │   │       │   ├── repository/
│       │   │       │   │   ├── TransactionRepository.kt
│       │   │       │   │   ├── CategoryRepository.kt
│       │   │       │   │   ├── BudgetRepository.kt
│       │   │       │   │   ├── PreferencesRepository.kt
│       │   │       │   │   └── BackupRepository.kt
│       │   │       │   └── usecase/
│       │   │       │       ├── transaction/
│       │   │       │       │   ├── AddTransactionUseCase.kt
│       │   │       │       │   ├── UpdateTransactionUseCase.kt
│       │   │       │       │   ├── DeleteTransactionUseCase.kt
│       │   │       │       │   ├── ObserveTransactionsUseCase.kt
│       │   │       │       │   └── ValidateTransactionUseCase.kt
│       │   │       │       ├── dashboard/
│       │   │       │       │   └── ObserveDashboardUseCase.kt
│       │   │       │       ├── category/
│       │   │       │       │   ├── ObserveCategoriesUseCase.kt
│       │   │       │       │   ├── SaveCategoryUseCase.kt
│       │   │       │       │   └── ArchiveCategoryUseCase.kt
│       │   │       │       ├── budget/
│       │   │       │       │   ├── SaveBudgetUseCase.kt
│       │   │       │       │   └── ObserveBudgetsUseCase.kt
│       │   │       │       ├── report/
│       │   │       │       │   └── GenerateReportUseCase.kt
│       │   │       │       └── backup/
│       │   │       │           ├── ExportCsvUseCase.kt
│       │   │       │           ├── ExportBackupUseCase.kt
│       │   │       │           └── ImportBackupUseCase.kt
│       │   │       │
│       │   │       ├── data/
│       │   │       │   ├── local/
│       │   │       │   │   ├── ExpenseDatabase.kt
│       │   │       │   │   ├── entity/
│       │   │       │   │   │   ├── TransactionEntity.kt
│       │   │       │   │   │   ├── CategoryEntity.kt
│       │   │       │   │   │   └── BudgetEntity.kt
│       │   │       │   │   ├── dao/
│       │   │       │   │   ├── TransactionDao.kt
│       │   │       │   │   ├── CategoryDao.kt
│       │   │       │   │   └── BudgetDao.kt
│       │   │       │   ├── relation/
│       │   │       │   │   └── TransactionWithCategory.kt
│       │   │       │   ├── migration/
│       │   │       │   │   └── DatabaseMigrations.kt
│       │   │       │   ├── mapper/
│       │   │       │   │   ├── TransactionMapper.kt
│       │   │       │   │   ├── CategoryMapper.kt
│       │   │       │   │   └── BudgetMapper.kt
│       │   │       │   └── impl/
│       │   │       │       ├── TransactionRepositoryImpl.kt
│       │   │       │       ├── CategoryRepositoryImpl.kt
│       │   │       │       ├── BudgetRepositoryImpl.kt
│       │   │       │       ├── PreferencesRepositoryImpl.kt
│       │   │       │       └── BackupRepositoryImpl.kt
│       │   │       │
│       │   │       ├── ui/
│       │   │       │   ├── navigation/
│       │   │       │   │   ├── AppNavigation.kt
│       │   │       │   │   ├── AppRoute.kt
│       │   │       │   │   └── BottomNavigationBar.kt
│       │   │       │   ├── theme/
│       │   │       │   │   ├── Color.kt
│       │   │       │   │   ├── Theme.kt
│       │   │       │   │   └── Type.kt
│       │   │       │   ├── components/
│       │   │       │   │   ├── AppTopBar.kt
│       │   │       │   │   ├── AppScaffold.kt
│       │   │       │   │   ├── PrimaryButton.kt
│       │   │       │   │   ├── AmountText.kt
│       │   │       │   │   ├── SummaryCard.kt
│       │   │       │   │   ├── TransactionRow.kt
│       │   │       │   │   ├── CategoryIcon.kt
│       │   │       │   │   ├── EmptyState.kt
│       │   │       │   │   ├── LoadingState.kt
│       │   │       │   │   ├── ErrorState.kt
│       │   │       │   │   ├── ConfirmDialog.kt
│       │   │       │   │   └── MonthSelector.kt
│       │   │       │   │
│       │   │       │   ├── dashboard/
│       │   │       │   │   ├── DashboardScreen.kt
│       │   │       │   │   ├── DashboardViewModel.kt
│       │   │       │   │   └── DashboardUiState.kt
│       │   │       │   ├── transactions/
│       │   │       │   │   ├── TransactionListScreen.kt
│       │   │       │   │   ├── TransactionListViewModel.kt
│       │   │       │   │   ├── TransactionListUiState.kt
│       │   │       │   │   ├── TransactionFormScreen.kt
│       │   │       │   │   ├── TransactionFormViewModel.kt
│       │   │       │   │   └── TransactionFormUiState.kt
│       │   │       │   ├── categories/
│       │   │       │   │   ├── CategoriesScreen.kt
│       │   │       │   │   ├── CategoriesViewModel.kt
│       │   │       │   │   └── CategoryFormDialog.kt
│       │   │       │   ├── budgets/
│       │   │       │   │   ├── BudgetsScreen.kt
│       │   │       │   │   ├── BudgetsViewModel.kt
│       │   │       │   │   ├── BudgetsUiState.kt
│       │   │       │   │   └── BudgetFormDialog.kt
│       │   │       │   ├── reports/
│       │   │       │   │   ├── ReportsScreen.kt
│       │   │       │   │   ├── ReportsViewModel.kt
│       │   │       │   │   ├── ReportsUiState.kt
│       │   │       │   │   └── ReportCharts.kt
│       │   │       │   └── settings/
│       │   │       │       ├── SettingsScreen.kt
│       │   │       │       ├── SettingsViewModel.kt
│       │   │       │       └── SettingsUiState.kt
│       │   │       │
│       │   │       └── platform/
│       │   │           ├── export/
│       │   │           │   ├── CsvExporter.kt
│       │   │           │   └── BackupDocumentHandler.kt
│       │   │           └── import/
│       │   │               └── BackupDocumentReader.kt
│       │   │
│       │   ├── res/
│       │   │   ├── drawable/
│       │   │   ├── mipmap-hdpi/
│       │   │   ├── mipmap-mdpi/
│       │   │   ├── mipmap-xhdpi/
│       │   │   ├── mipmap-xxhdpi/
│       │   │   ├── mipmap-xxxhdpi/
│       │   │   ├── values/
│       │   │   │   ├── strings.xml
│       │   │   │   ├── colors.xml
│       │   │   │   └── themes.xml
│       │   │   └── xml/
│       │   │       └── backup_rules.xml
│       │   └── assets/
│       │
│       ├── test/
│       │   └── java/com/example/offlineexpense/
│       │       ├── core/money/
│       │       ├── domain/usecase/
│       │       ├── data/impl/
│       │       └── ui/
│       │
│       └── androidTest/
│           └── java/com/example/offlineexpense/
│               ├── data/local/
│               ├── data/dao/
│               └── ui/
```

The tree defines responsibilities and intended file locations. Create all required files, but do not create empty files merely to match the tree.

If an equivalent abstraction can be implemented cleanly with fewer files, combine tightly related implementations without violating separation of concerns. Update all package declarations, imports, and documentation consistently.

## 3.3 Dependency Injection

Use Hilt for dependency injection.

Implement:

- Application class annotated with `@HiltAndroidApp`.
- Main activity configured for Hilt.
- Database provider.
- DAO providers through the database.
- Repository bindings.
- Dispatcher provider where useful.
- Hilt ViewModel construction.

Provide singleton database and repository instances where appropriate.

Do not manually construct ViewModels inside composables.

Do not use a service locator or global mutable singleton to bypass dependency injection.

## 3.4 Navigation

Create a typed or otherwise strongly structured route system compatible with the selected Navigation Compose version.

Required destinations:

- Dashboard.
- Transactions.
- Add transaction.
- Edit transaction.
- Categories.
- Budgets.
- Reports.
- Settings.

The add and edit forms must support the relevant transaction ID or navigation argument.

Prevent duplicate navigation when users repeatedly tap the same action.

Handle Android system Back navigation correctly.

Preserve navigation state sensibly when switching between top-level sections.

The selected bottom-navigation item must always match the current destination.

## 3.5 ViewModel State Management

Each screen must expose an immutable state model using `StateFlow`.

Represent important screen conditions explicitly:

- Initial loading.
- Content loaded.
- Empty content.
- Recoverable error.
- Form validation errors.
- Operation in progress.
- Operation success where confirmation is appropriate.

Keep navigation events, snackbar events, and one-time user messages separate from persistent screen state when appropriate.

Do not mutate Compose state from background threads.

Do not use blocking database operations on the main thread.

---

# 4. DATA SCHEMA & PERSISTENCE

## 4.1 General Database Requirements

Use Room with SQLite.

Name the database:

`expense_tracker.db`

Use a database class named `ExpenseDatabase`.

The initial database version must be `1`.

Enable Room schema export and commit generated schemas to source control.

Register explicit migrations whenever the schema changes.

**Never use destructive migration as a production fallback.** A database upgrade must not silently delete financial records.

Perform all database operations asynchronously using suspend functions or Flow.

Use foreign keys, indexes, appropriate uniqueness constraints, and `@Transaction` for operations that must be atomic.

## 4.2 Money Storage Policy

Never store persisted monetary amounts as `Float` or `Double`.

Store monetary amounts as a positive `Long` representing the smallest standard unit of the configured currency.

Example for INR:

- ₹100.00 is stored as `10000`.
- ₹25.50 is stored as `2550`.
- ₹0.75 is stored as `75`.

Default the app currency to INR unless a different default is already established in the project.

Use `java.util.Currency` or a reliable platform-supported equivalent to determine currency fraction digits.

Use `BigDecimal` during parsing and conversion.

Validate precision before converting to minor units. Do not silently truncate excessive decimal places or overflow a `Long`.

Amounts persisted for transactions and budgets must be strictly greater than zero.

Store transaction direction separately as `EXPENSE` or `INCOME`.

Never represent income by inserting negative amounts.

Document that changing the application's currency after data exists must not reinterpret old amounts. The simplest acceptable policy is to allow currency changes only when the database contains no financial records, or to require a clear, validated conversion workflow before making such a change.

## 4.3 Table: `categories`

Create `CategoryEntity`.

Fields:

| Field | Type | Constraints |
|---|---|---|
| id | Long | Primary key, auto-generated |
| name | String | Required, trimmed, nonblank |
| type | String | `EXPENSE` or `INCOME` |
| iconKey | String | Required, valid internal icon identifier |
| colorHex | String | Required, validated color value |
| isDefault | Boolean | Required |
| isArchived | Boolean | Required |
| createdAtEpochMillis | Long | Required |
| updatedAtEpochMillis | Long | Required |

Requirements:

- Use `id` as the primary key.
- Index category type and archive status when query patterns justify the index.
- Prevent blank category names.
- Disallow duplicate active category names within the same transaction type, using a case-insensitive normalization or validation strategy.
- Do not allow deletion of a category when it is actively referenced by a budget. Prefer archiving it.
- Allow transactions belonging to an archived category to remain visible in historical records.
- Do not allow selecting archived categories for new transactions.

Seed useful default categories on the first installation.

Suggested expense categories:

- Food & Dining.
- Groceries.
- Transportation.
- Shopping.
- Housing.
- Bills & Utilities.
- Health.
- Education.
- Entertainment.
- Travel.
- Personal Care.
- Other Expense.

Suggested income categories:

- Salary.
- Freelance.
- Business.
- Investments.
- Gifts.
- Other Income.

Keep default-category seeding idempotent. Running initialization again must not insert duplicate categories.

Use appropriate built-in Material icons or custom vector resources.

## 4.4 Table: `transactions`

Create `TransactionEntity`.

Fields:

| Field | Type | Constraints |
|---|---|---|
| id | Long | Primary key, auto-generated |
| title | String | Required, trimmed, nonblank |
| amountMinor | Long | Required, greater than zero |
| type | String | `EXPENSE` or `INCOME` |
| categoryId | Long? | Nullable foreign key to categories |
| paymentMethod | String | Valid enum identifier |
| merchant | String? | Optional, trimmed |
| note | String? | Optional, trimmed |
| occurredAtEpochMillis | Long | Required |
| createdAtEpochMillis | Long | Required |
| updatedAtEpochMillis | Long | Required |

Constraints and indexes:

- Foreign key references `categories.id`.
- Use a `SET_NULL` delete policy if a referenced category is genuinely removed; the default UI should prefer archiving instead.
- Index `occurredAtEpochMillis`.
- Index `categoryId`.
- Index `type`.
- Add a compound index for common history filters when justified.

Define a typed `TransactionType` enum containing:

- `EXPENSE`
- `INCOME`

Define a `PaymentMethod` enum containing:

- `CASH`
- `CARD`
- `BANK_TRANSFER`
- `UPI`
- `OTHER`

Persist stable enum string identifiers rather than ordinal positions.

For unexpected or unsupported persisted enum values, handle conversion safely and explicitly. Never silently misclassify an expense as income.

An uncategorized transaction must remain valid.

## 4.5 Table: `budgets`

Create `BudgetEntity`.

This table stores monthly category budgets.

| Field | Type | Constraints |
|---|---|---|
| id | Long | Primary key, auto-generated |
| categoryId | Long | Required foreign key to categories |
| yearMonth | String | Required, ISO format `YYYY-MM` |
| limitMinor | Long | Required, greater than zero |
| createdAtEpochMillis | Long | Required |
| updatedAtEpochMillis | Long | Required |

Required constraints:

- Unique combination of `categoryId` and `yearMonth`.
- Foreign key references `categories.id`.
- Index `yearMonth`.
- Index `categoryId`.
- Validate that budgets reference expense categories, not income categories.
- Reject invalid month keys and nonpositive budget limits.
- Do not create duplicate budgets for the same category and month.

When a budget already exists for a category and month, update the existing record rather than inserting a duplicate.

Use the application's configured currency.

## 4.6 Data Models and Mappers

Maintain separate domain models and Room entities.

Implement explicit mapping functions for:

- Transaction entity to domain transaction.
- Domain transaction to entity.
- Category entity to domain category.
- Domain category to entity.
- Budget entity to domain budget.
- Domain budget to entity.

Do not expose Room entities directly as UI models unless a well-justified implementation detail makes this unavoidable.

Ensure enum conversion, nullable fields, currency amounts, and timestamps are handled consistently.

## 4.7 Required DAO Operations

### TransactionDao

Implement operations equivalent to:

- Observe all transactions, ordered by occurrence date descending.
- Observe a transaction by ID.
- Insert a transaction.
- Update a transaction.
- Delete a transaction.
- Observe transactions within an inclusive/exclusive timestamp range.
- Observe transactions filtered by transaction type.
- Search title, merchant, and notes.
- Filter by category.
- Filter by payment method.
- Apply combinations of query text, date range, type, category, and payment method.
- Calculate total income in a given date range.
- Calculate total expenses in a given date range.
- Count transactions when required.
- Aggregate spending by category.
- Aggregate income and expenses for reporting periods.
- Obtain the most recent transactions for the dashboard.

Use Flow for observations that should automatically update when database records change.

Use parameterized Room queries or safe query construction; do not concatenate untrusted search text into SQL.

All aggregate results must handle empty tables correctly and return zero or an explicit empty value rather than null crashes.

### CategoryDao

Implement:

- Observe active categories.
- Observe categories by transaction type.
- Observe categories including archived ones for historical display and management.
- Find a category by ID.
- Insert and update categories.
- Archive and unarchive categories.
- Check duplicate names.
- Retrieve default categories.
- Insert default categories without duplication.

### BudgetDao

Implement:

- Observe budgets for a selected month.
- Observe all saved budgets.
- Retrieve a budget by category and month.
- Insert a budget.
- Update a budget.
- Delete a budget.
- Retrieve budget limits joined with relevant category information.
- Calculate actual expense totals for each budget period.

Budget progress must use actual expense transactions for the relevant category and month, not income, unrelated transactions, or records from adjacent months.

## 4.8 Financial Calculation Rules

Implement consistent calculations for every screen.

### Balance

`Balance = Total Income - Total Expenses`

### Expense Total

Sum the positive minor-unit amounts of transactions whose type is `EXPENSE` within the selected period.

### Income Total

Sum the positive minor-unit amounts of transactions whose type is `INCOME` within the selected period.

### Budget Remaining

`Budget Remaining = Budget Limit - Actual Expenses`

### Budget Usage

`Budget Usage = Actual Expenses / Budget Limit`

Clamp the visual progress indicator to the range 0.0–1.0, but retain the true calculated usage for labels and over-budget indicators.

If expenses exceed the budget, display the true over-budget amount rather than pretending the spending stopped at 100%.

All monetary aggregates must use safe `Long` arithmetic or an appropriate overflow-safe strategy.

Handle empty date ranges, month boundaries, leap years, device locale, and device time zone correctly.

For each selected month, calculate its local start and exclusive end timestamps from the calendar. Do not approximate months as 30 days.

When grouping records by date, month, or year, ensure the logic is consistent with the application's local calendar and documented time-zone policy.

## 4.9 Transaction Safety and Database Consistency

Adding or updating a transaction must validate that:

- The title is not blank.
- The amount is valid and greater than zero.
- The transaction type is valid.
- The currency precision is valid.
- The category exists and is active, if selected.
- The category type matches the transaction type.
- The payment method is valid.
- The date is valid and within supported platform date ranges.

Use Room transactions for operations involving multiple related writes.

A failed write must not partially update financial data.

Handle database errors using domain-level error results and present understandable messages to the user.

## 4.10 Preferences

Use DataStore for nonfinancial UI preferences.

Persist:

- Theme selection: `SYSTEM`, `LIGHT`, `DARK`.
- Currency code.
- Whether onboarding or first-run guidance was completed.
- Any additional justified presentation preferences.

Default to system theme.

Default currency to INR for a new installation.

Do not put transaction history or budgets in DataStore; they belong in Room.

## 4.11 CSV Export

Implement a complete CSV exporter that includes:

- Transaction ID.
- Date and time.
- Title.
- Type.
- Category.
- Amount.
- Currency code.
- Payment method.
- Merchant.
- Note.

Requirements:

- Correct CSV escaping for commas, double quotes, and newlines.
- Correct header row.
- Stable date formatting.
- Deterministic amount formatting.
- UTF-8 encoding.
- Safe handling of empty fields.
- Appropriate filename such as `expense_tracker_YYYY-MM-DD.csv`.
- No silent truncation.

Use Android's `ACTION_CREATE_DOCUMENT` or the appropriate Activity Result API to let the user choose the destination.

Display success or failure feedback after the operation completes.

## 4.12 JSON Backup and Restore

Implement a versioned JSON backup format containing:

- Backup format version.
- Export timestamp.
- Currency metadata.
- Categories.
- Transactions.
- Budgets.
- Required record identifiers and timestamps.

Only include fields that are necessary to restore the complete financial dataset.

Validate imported JSON before changing the database.

Reject:

- Unsupported format versions.
- Missing required fields.
- Invalid enum values.
- Negative or zero transaction amounts.
- Invalid currency metadata.
- Invalid dates or month keys.
- Missing category references that cannot be reconciled.
- Duplicate IDs or conflicting records.
- Unreasonably large or malformed files that could exhaust device memory.

Implement restore as an atomic database operation.

Offer clear confirmation before replacing existing data.

Do not silently merge incompatible datasets or overwrite existing financial records.

If merge functionality is implemented, document deterministic conflict resolution and ensure IDs and foreign keys remain consistent.

Use the Storage Access Framework rather than broad storage permissions.

## 4.13 Database Initialization and Migration

Create a reliable database initialization process.

- Seed default categories exactly once or idempotently.
- Avoid blocking the main thread.
- Avoid race conditions between initialization and the first transaction form.
- Configure Room migration registration explicitly.
- Preserve data across application upgrades.
- Export schema files.
- Test all available migration paths whenever migrations are added.

Do not seed transactions, budgets, or fake financial history.

---

# 5. UI/UX SPECIFICATIONS

## 5.1 Design Direction

Create a polished, premium-quality personal finance app that feels native to Android.

The visual style should be modern, minimal, calm, professional, and easy to understand for everyday users.

Do not create a generic unfinished Material template.

Use Material 3 as the foundation, with consistent spacing, typography, iconography, surfaces, and navigation.

Recommended visual identity:

- Primary color: deep emerald green.
- Secondary color: muted teal.
- Accent color: soft mint.
- Background: warm off-white in light mode.
- Surface: white or near-white.
- Main text: dark charcoal.
- Secondary text: muted grey.
- Expense indicators: restrained red.
- Income indicators: green.
- Budget caution: amber.
- Error indicators: accessible red.

Choose colors with accessible contrast and define them centrally in the theme files.

Support both light and dark mode.

In dark mode, use deep neutral surfaces with clearly differentiated cards, muted borders, and readable text. Do not simply invert every light-theme color.

Support dynamic color where appropriate without making the design inconsistent or inaccessible.

Use rounded cards and buttons with consistent corner radii. Avoid excessive shadows, visual clutter, oversized gradients, decorative animations, and unnecessary borders.

## 5.2 Global Layout

Use a single main activity and a reusable application scaffold.

The primary mobile navigation should contain four sections:

1. Home.
2. Transactions.
3. Budgets.
4. Reports.

Provide access to Categories and Settings through suitable navigation actions, such as a top app-bar action or an organized settings/menu destination.

Use a prominent floating action button or equivalent primary action for adding a transaction.

The primary action must remain easy to access without covering important content.

Use `WindowInsets` APIs correctly so content does not overlap the status bar, navigation bar, or system gesture area.

All screens must scroll appropriately on compact devices.

Support portrait layouts first, with sensible adaptive behavior for landscape and larger screens.

Use stable keys for transaction lists.

Do not hardcode a single screen width.

## 5.3 Dashboard Screen

The dashboard is the first screen shown after application startup.

It must display real data from Room.

### Header

Show:

- A concise greeting or application title.
- The currently selected month.
- A working month selector.
- A settings action.

The month selector must allow navigation between months without losing the current database state.

Do not prevent viewing historical months simply because they are in the past.

### Financial Summary

Display three clear summary cards:

**Total Balance**
- Calculated income minus expenses for the selected reporting period.
- Format with the configured currency.
- If the balance is negative, display it clearly without crashing or hiding the minus sign.

**Income**
- Sum of income transactions for the selected period.
- Use an income visual indicator.

**Expenses**
- Sum of expense transactions for the selected period.
- Use an expense visual indicator.

Label the reporting period clearly so users know whether the values represent the current month or another selected period.

### Expense Overview

Include:

- A category spending breakdown.
- A meaningful chart or progress visualization.
- Total spending for the selected period.
- Clear labels and formatted values.

If there are no expenses for the selected period, show a helpful empty state rather than an empty chart with unexplained axes.

### Recent Transactions

Show the most recent few transactions, ordered by their occurrence time descending.

Each row should contain:

- Category icon.
- Transaction title.
- Category or payment method.
- Relevant date.
- Formatted amount.
- A clear income or expense visual indicator.

Tapping a row must open its edit form.

Provide a working action to view all transactions.

### Quick Action

Provide an easily accessible Add Transaction action.

No financial values on the dashboard may be hardcoded.

All dashboard summaries must react to Room database changes without restarting the application.

## 5.4 Transaction List Screen

Create a complete transaction history screen.

### Header

Display a clear page title and an action for adding a transaction.

### Search

Provide a working search field.

Search transaction title, merchant, and note fields.

Search must update the visible results without requiring the user to restart the app or manually refresh the list.

Debounce rapid query changes when useful, and do not block the main thread.

### Filters

Support these filters:

- All.
- Expenses.
- Income.
- Current month or a selected date range.
- Category.
- Payment method.

Allow the user to clear active filters easily.

Make it visually obvious when filtering is active.

### Grouping

Group transaction rows by local calendar date or provide clear date separators.

Each group should show an appropriately formatted date heading.

Do not incorrectly classify transactions around midnight or month boundaries.

### Transaction Rows

Each row should include:

- Category icon.
- Title.
- Category.
- Date and optional time.
- Amount.
- Income or expense indicator.

Tapping a row opens the edit screen.

Support deletion using an explicit confirmation dialog.

Never delete a record merely because a row was accidentally tapped.

### Empty and Error States

When there are no transactions, present a friendly message and a clear Add Transaction action.

When a search produces no matches, explain that no results match the current query or filters.

When data cannot be loaded, provide a recoverable error state and retry action where appropriate.

The screen must never display fictitious sample transactions.

## 5.5 Add and Edit Transaction Screen

This is one of the most important screens. Implement its complete behavior.

### Form Fields

Include:

1. Transaction type selector: Expense or Income.
2. Amount input.
3. Title input.
4. Category selector.
5. Date selector.
6. Optional time selection if appropriate.
7. Payment method selector.
8. Optional merchant field.
9. Optional note field.
10. Save action.
11. Cancel or Back action.

### Amount Input

Use a decimal-compatible keyboard.

The field must:

- Accept valid amounts.
- Reject malformed monetary input.
- Reject zero and negative amounts.
- Respect currency precision.
- Reject overflow.
- Avoid silently accepting excess decimal places.
- Display field-level validation messages.
- Preserve input when validation fails.

Do not use a locale-independent number parser that incorrectly interprets decimal separators for all users.

Use a currency-aware parser and formatter.

### Type Selection

When the user switches between Expense and Income:

- Update the eligible category list.
- Preserve the amount when safe.
- Clear an incompatible category or require a new selection.
- Keep the current form values otherwise intact.

Prevent an income transaction from being saved under an expense-only category, and vice versa.

### Category Selection

Display category names and icons in a clean bottom sheet, dropdown, or selection screen.

Show only active categories applicable to the selected transaction type.

Provide a convenient way to manage categories.

Allow the transaction to remain uncategorized if this is part of the product's intended behavior.

### Date Selection

Use a native-feeling date picker.

Support past transaction dates and reasonable future dates, subject to a documented validation policy.

Ensure the chosen date is persisted correctly and displayed consistently across screens.

### Editing

When editing an existing transaction:

- Load the correct database record.
- Prepopulate every supported field.
- Preserve its identifier and creation timestamp.
- Update its modification timestamp.
- Save changes to the existing record instead of creating a duplicate.
- Show success feedback only after the database operation succeeds.

Prevent repeated taps on Save from inserting duplicate transactions.

### Cancellation

If the user has changed fields, prevent accidental loss of unsaved work where appropriate. Use a confirmation dialog when necessary.

### Validation Feedback

Display clear errors near invalid fields.

Do not rely solely on a generic error toast.

Disable the Save button during an active save operation or otherwise enforce duplicate-submission protection.

## 5.6 Categories Screen

Implement category management.

Provide separate Expense and Income category sections.

Each category row should display:

- Icon.
- Name.
- Type.
- Optional spending total for the current selected month.
- Overflow menu.

Allow users to:

- Create custom categories.
- Rename categories.
- Change icon and color.
- Archive and restore categories.
- View default categories.

Validate duplicate names, blank names, and invalid colors.

Default categories must be handled safely. Do not allow destructive actions that unexpectedly orphan budgets or hide historical transaction information.

Archived categories must remain visible on existing transaction records.

New transactions must not offer archived categories as available choices.

Use a form dialog or dedicated form screen with proper validation and accessibility.

## 5.7 Budgets Screen

Implement monthly budget management.

### Month Selection

Allow users to choose a month and inspect the budgets configured for that month.

### Budget Cards

Each card must display:

- Category name and icon.
- Budget limit.
- Actual spending.
- Remaining budget or overspent amount.
- Progress bar.
- Usage percentage.

Calculate values from actual expense transactions and the corresponding budget period.

Use a normal progress color below a sensible caution threshold, amber near the limit, and red when the budget is exceeded.

Never rely only on color. Include textual labels such as `75% used` or `Over budget by ...`.

### Add and Edit Budget

Provide a form with:

- Expense category.
- Month.
- Budget amount.
- Save action.

Validate all input.

Enforce a single budget for each category and month.

If a matching budget already exists, edit the existing record.

Prevent budgets for income categories.

### Budget Without Transactions

A budget with no spending must display zero spending and zero usage.

Do not treat missing data as an error.

### Delete Budget

Require confirmation before removing a saved budget.

Deleting a budget must not delete related financial transactions.

## 5.8 Reports Screen

Build a useful reporting interface backed by actual stored data.

### Period Selection

Provide selectable reporting periods:

- This week.
- This month.
- Last month.
- This year.
- Custom date range.

Ensure all calculations use the exact selected boundaries.

### Summary

Display:

- Total income.
- Total expenses.
- Net balance.
- Transaction count.

### Expense Category Breakdown

Provide a readable category breakdown with:

- Category icon or color marker.
- Category name.
- Expense total.
- Share of total expenses.
- Optional percentage label.

Use a donut chart or a well-designed horizontal bar visualization.

If the total expense value is zero, show a sensible empty visualization state.

### Income Versus Expense

Provide a visual comparison of income and expenses for the selected period.

### Spending Trend

Provide a chronological trend chart for suitable periods.

Choose daily, weekly, or monthly intervals that match the date range.

Label the axes clearly.

Use real aggregate queries or tested domain calculations.

Avoid generating misleading data points for periods where no transactions occurred.

### Chart Accessibility

Charts must include readable legends, meaningful text summaries, and appropriate content descriptions.

Do not communicate financial information through color alone.

Charts must resize for different phone widths and remain usable in dark mode.

## 5.9 Settings Screen

Provide a structured settings interface.

### Appearance

Offer:

- System default theme.
- Light theme.
- Dark theme.

Apply changes immediately and persist the preference.

### Currency

Show the configured currency code and symbol.

Use valid ISO currency codes and appropriate fraction digits.

Make the consequences of changing currency clear. Do not silently convert or reinterpret historical records.

### Data Export

Provide an Export CSV action.

Launch the system document-creation flow.

Display success or failure feedback once writing finishes.

### Backup

Provide actions to:

- Create a JSON backup.
- Restore from a JSON backup.

Explain that the file contains private financial information.

Before destructive restore, show exactly what will happen to existing data and require confirmation.

Validate files before applying any changes.

### Privacy

Display a concise, honest statement explaining that transactions are stored locally and the app does not require an account or cloud synchronization.

Do not claim encryption or security features that have not been implemented.

### App Information

Display:

- Application name.
- App version.
- Short explanation of core functionality.

Do not include fake links, dead actions, or unnecessary decorative sections.

## 5.10 Global UI Components

Implement reusable composables for common interface elements.

### SummaryCard

A reusable card for balance, income, expense, and aggregate metrics.

### TransactionRow

A reusable and accessible transaction item that handles both income and expenses.

### AmountText

A dedicated amount component that uses the central money-formatting policy. It must never implement its own inconsistent monetary conversion.

### CategoryIcon

Display known, supported category icons and use a safe fallback for unknown icon identifiers.

### EmptyState

A reusable empty state with a title, explanation, and optional action.

### LoadingState

A restrained loading indicator for genuinely pending operations.

Avoid showing a full-screen spinner for every quick database observation.

### ErrorState

A readable message and appropriate retry or recovery action.

### ConfirmDialog

A reusable confirmation dialog for destructive operations, including transaction deletion and restore replacement.

### MonthSelector

A reusable month selection control with clear previous-month, next-month, and current-period actions.

All shared components must use theme colors and maintain consistent typography, spacing, and accessibility.

## 5.11 Interaction and Animation Requirements

Provide subtle, professional micro-interactions.

Examples:

- Animated navigation transitions where supported and appropriate.
- Smooth progress-bar updates.
- Short, restrained button interaction feedback.
- Subtle selection state transitions.
- Proper snackbar animations.
- Sensible bottom-sheet presentation.

Avoid:

- Excessive bouncing.
- Slow navigation.
- Long decorative animations.
- Animation that delays saving.
- Effects that reduce accessibility.
- Full-screen loading overlays for ordinary database updates.

Follow Android accessibility and reduced-motion considerations wherever practical.

## 5.12 Accessibility

Ensure:

- Interactive controls have meaningful content descriptions or accessible labels.
- Touch targets are approximately 48 dp or larger where practical.
- Text contrast is sufficient in both themes.
- Forms expose validation messages accessibly.
- Keyboard focus behaves logically.
- The UI works with large font sizes.
- Important information is not clipped.
- Charts have text equivalents.
- Error states are distinguishable from empty states.
- Icon-only controls have clear accessibility labels.

## 5.13 Empty, Loading, and Error Scenarios

Implement all important non-happy-path states.

The application must behave correctly when:

- No transactions exist.
- No categories exist because initialization is incomplete.
- A selected month has no transactions.
- A search returns no results.
- A budget has zero spending.
- A budget is exceeded.
- A CSV destination cannot be written.
- A backup file is malformed.
- The database operation fails.
- Currency formatting fails for an invalid currency code.
- A stored category has been archived.
- The user cancels an import or export operation.

Never allow one of these situations to crash the application.

---

# 6. EXECUTION SEQUENCE

Follow this exact implementation sequence. Complete and verify each stage before depending on it in the next stage.

Do not attempt to generate every file in one unverified step.

## Phase 1 — Inspect the Workspace and Establish the Build

1. Inspect the repository and determine whether it is new or already contains an application.
2. Identify existing package names, Gradle wrapper, Android Gradle Plugin, Kotlin, SDK configuration, and source directories.
3. Inspect available Android SDK and JDK installations if the environment allows it.
4. Select mutually compatible stable dependency versions.
5. Create or repair `settings.gradle.kts`.
6. Create or repair root `build.gradle.kts`.
7. Configure `gradle/libs.versions.toml`.
8. Configure `gradle.properties`.
9. Configure `app/build.gradle.kts`.
10. Verify basic Gradle project configuration and plugin resolution.

Do not implement ViewModels or composables until the build configuration supports their required dependencies.

**Gate:** The Gradle configuration and module structure must be coherent before proceeding.

## Phase 2 — Create Application Infrastructure

1. Create the Android manifest.
2. Create the application class.
3. Create `MainActivity`.
4. Configure Hilt.
5. Configure the application theme entry point.
6. Configure Room schema export.
7. Establish package naming and base application configuration.
8. Verify the application can compile with a minimal main activity.

Do not request network permissions.

**Gate:** A basic native Android application must compile successfully before adding complex layers.

## Phase 3 — Implement Core Domain Types

Create the platform-independent domain models first.

Implement:

1. `TransactionType`.
2. `PaymentMethod`.
3. `Transaction`.
4. `Category`.
5. `Budget`.
6. `DashboardSummary`.
7. Report models.
8. Date-range model.
9. Result and error types.
10. Currency and amount validation contracts.

Define clear invariants before connecting any persistence layer.

Use appropriate immutable data classes and explicit nullability.

**Gate:** Domain models must compile independently of the Compose UI.

## Phase 4 — Implement Money and Date Utilities

Implement and test:

- Currency-aware amount parsing.
- Conversion to minor units.
- Formatting from minor units.
- Currency precision validation.
- Overflow handling.
- Local date-range boundaries.
- Month start and end calculations.
- Week calculations.
- Date display formatting.

Test zero, invalid text, negative numbers, extra decimal places, large amounts, leap years, month boundaries, and empty reporting periods.

Do not continue with financial aggregation until money conversion has passed its tests.

## Phase 5 — Implement Room Entities and Database

Create:

1. `CategoryEntity`.
2. `TransactionEntity`.
3. `BudgetEntity`.
4. Any required Room relationship data classes.
5. `TransactionDao`.
6. `CategoryDao`.
7. `BudgetDao`.
8. `ExpenseDatabase`.
9. Database migrations infrastructure.
10. Default category seeding.

Implement database constraints, indexes, ordering, filtering, search, and aggregation queries.

Keep all SQL queries complete and compatible with the selected Room version.

Do not use destructive migrations.

**Gate:** Compile the database layer and validate query compatibility through Room's annotation processing.

## Phase 6 — Implement Repository Interfaces

Create repository contracts for:

- Transactions.
- Categories.
- Budgets.
- Preferences.
- Backup and restore.

Use domain models and domain-level types in repository interfaces wherever practical.

Define expected error handling and observable update behavior.

Do not expose Android-specific APIs from domain repository contracts without a clear need.

## Phase 7 — Implement Repository Implementations and Dependency Injection

Create:

- Entity/domain mappers.
- Transaction repository implementation.
- Category repository implementation.
- Budget repository implementation.
- Preferences repository implementation.
- Database and repository Hilt modules.

Verify that:

- DAO data is mapped consistently.
- Writes validate required domain invariants.
- Flow emissions reflect database changes.
- Category-type mismatches are rejected.
- Database exceptions are converted into appropriate errors.
- Default category seeding is idempotent.

**Gate:** Repository tests must prove that stored and observed data behave correctly before UI implementation begins.

## Phase 8 — Implement Use Cases and Financial Calculations

Implement the required use cases for:

- Adding transactions.
- Updating transactions.
- Deleting transactions.
- Observing and filtering transactions.
- Validating transactions.
- Observing dashboard summaries.
- Managing categories.
- Managing budgets.
- Generating reports.
- Exporting CSV.
- Exporting backups.
- Importing backups.

Keep calculation policies consistent across dashboard, budgets, and reports.

Avoid duplicating different versions of income, expense, or balance calculations across multiple ViewModels.

Write unit tests for each critical financial rule.

**Gate:** The primary business logic must pass unit tests before being connected to the UI.

## Phase 9 — Implement the Theme and Shared Compose Components

Create:

- Color definitions.
- Typography.
- Material 3 theme.
- Light palette.
- Dark palette.
- App scaffold.
- Top app bar.
- Bottom navigation.
- Amount text.
- Summary cards.
- Transaction rows.
- Category icons.
- Empty, loading, and error states.
- Confirmation dialog.
- Month selector.
- Reusable input components.

Use previews where they materially help design verification.

Do not put business logic inside shared presentation components.

Verify readable layouts in both light and dark modes.

## Phase 10 — Implement Navigation

Create the route definitions and navigation graph.

Implement:

- Correct destination arguments.
- Dashboard navigation.
- Transaction list navigation.
- Add transaction navigation.
- Edit transaction navigation.
- Category management navigation.
- Budget navigation.
- Report navigation.
- Settings navigation.
- Correct Back behavior.
- Appropriate selected navigation state.

Ensure navigation destinations reference files that already exist.

**Gate:** All routes must compile and lead to real screen implementations.

## Phase 11 — Implement the Dashboard

Build the dashboard ViewModel and UI state first.

Connect it to database-backed use cases.

Then implement the screen.

Verify:

- Real income and expense totals.
- Correct net balance.
- Month selection.
- Recent transaction ordering.
- Actual spending breakdown.
- Empty-state behavior.
- Live updates after database changes.
- Dark-mode compatibility.

Never introduce permanent dummy data to make the dashboard appear populated.

## Phase 12 — Implement Transaction Creation, Editing, and Deletion

Implement the transaction form UI state and ViewModel.

Then build:

1. Add form.
2. Edit form.
3. Amount validation.
4. Category selection.
5. Date selection.
6. Payment method selection.
7. Save handling.
8. Update handling.
9. Delete confirmation.
10. Success and failure feedback.

Test process recreation and navigation arguments where relevant.

Prevent double submissions.

Verify that a transaction is persisted exactly once and appears immediately in the dashboard and list.

## Phase 13 — Implement Transaction History and Search

Build the complete transaction list.

Implement combined filtering by:

- Text.
- Date range.
- Type.
- Category.
- Payment method.

Verify:

- Correct date ordering.
- Correct amounts and sign presentation.
- Correct category labels.
- Search with punctuation and case variations.
- Empty search results.
- Clearing filters.
- Editing from a row.
- Deletion confirmation.
- UI responsiveness with a large transaction history.

## Phase 14 — Implement Category Management

Build the categories ViewModel, forms, and screen.

Implement creation, editing, archiving, restoring, validation, and duplicate-name checks.

Verify that:

- New categories survive app restarts.
- Archived categories are unavailable for new transactions.
- Historical transactions remain understandable.
- Category-type mismatches cannot be saved.
- Existing budgets remain consistent.

## Phase 15 — Implement Budget Management

Build budget state management and UI.

Connect budget records with the relevant expense aggregates.

Verify:

- One budget per category and month.
- Editing updates rather than duplicates.
- Zero-spending behavior.
- Partial budget usage.
- Exactly-at-limit behavior.
- Over-budget behavior.
- Correct month boundaries.
- Switching between reporting months.
- Database updates refresh the visual progress.

## Phase 16 — Implement Reporting

Implement report queries or tested domain aggregation.

Build the reporting ViewModel before the visualization layer.

Implement:

- Period selection.
- Custom date range.
- Income and expense summary.
- Net balance.
- Expense category breakdown.
- Income-versus-expense chart.
- Trend chart.

Test charts against known transaction datasets.

Validate that the visualized totals equal the displayed financial summaries.

Do not use randomly generated chart values.

## Phase 17 — Implement Export, Import, and Preferences

Implement CSV export and validate escaping behavior.

Implement JSON serialization using an explicit, versioned backup model.

Build document-picker integration using Android Activity Result APIs and the Storage Access Framework.

Implement strict import validation before mutation.

Run restore inside a transaction, where the chosen Room operations permit it.

Add confirmation and feedback states.

Implement persisted theme and currency preferences.

Verify that no unnecessary storage permissions are requested.

## Phase 18 — Integrate and Verify the Entire Application

Test the complete user journey:

1. Install and launch the app.
2. View the empty dashboard.
3. Add an expense.
4. Add an income transaction.
5. Confirm totals update.
6. Edit a transaction.
7. Delete a transaction after confirmation.
8. Create a category.
9. Archive and restore a category.
10. Set a monthly budget.
11. Add expenses against that budget.
12. Confirm budget progress updates.
13. Search transactions.
14. Filter transactions by type and date.
15. Generate a report.
16. Change the theme.
17. Export a CSV file.
18. Create a JSON backup.
19. Restore a backup after confirmation.
20. Restart the application and verify persistence.
21. Repeat the main journey in airplane mode.

Verify that the application has no hidden dependence on a network connection.

## Phase 19 — Automated Testing

Implement and run tests for the following areas.

### Money Tests

- Valid integer amounts.
- Valid decimal amounts.
- Invalid text.
- Zero.
- Negative amounts.
- Excess precision.
- Currency-specific fraction digits.
- Overflow boundaries.
- Formatting.

### Domain Tests

- Balance calculations.
- Income totals.
- Expense totals.
- Budget usage.
- Over-budget calculations.
- Transaction validation.
- Category and transaction type matching.
- Reporting-period boundaries.

### Room Tests

Use an in-memory Room database where appropriate.

Test:

- Inserting and reading transactions.
- Updating transactions.
- Deleting transactions.
- Foreign-key behavior.
- Category queries.
- Budget uniqueness.
- Monthly aggregate queries.
- Search and filtering.
- Default category seeding.
- Transactional restore behavior where applicable.

### ViewModel Tests

Test:

- Initial loading state.
- Successful data load.
- Empty states.
- Validation failures.
- Save operations.
- Database errors.
- State updates after repository changes.
- Filter combinations.

### Compose UI Tests

Test key user flows:

- Main navigation.
- Adding an expense.
- Adding income.
- Editing a transaction.
- Deleting a transaction.
- Empty history.
- Budget creation.
- Theme behavior where practical.
- Search and filtering.

Use fake repositories only in tests, never as a substitute for production persistence.

## Phase 20 — Final Build, Quality Checks, and Delivery

Run the relevant Gradle tasks supported by the environment, including:

- Debug Kotlin compilation.
- Debug Android build.
- Unit tests.
- Android lint.
- Instrumentation tests when an appropriate emulator or device is available.

Use the actual Gradle wrapper provided by the project.

Resolve compilation errors, dependency conflicts, unresolved imports, Room query validation errors, and runtime issues.

Do not suppress legitimate compiler or lint errors merely to achieve a successful build.

After the checks:

1. Inspect all required source files.
2. Verify there are no unfinished placeholder implementations.
3. Verify no production code uses fake financial data.
4. Verify app permissions.
5. Verify database migration policy.
6. Verify backup and import error handling.
7. Verify the README.
8. Generate the debug APK if the Android build environment supports it.
9. Report the actual test and build results.
10. Clearly list any checks that could not be executed because the environment lacked a device, emulator, SDK, or other necessary resource.

Do not claim that the APK was generated unless the build output confirms its existence.

---

# FINAL ACCEPTANCE CRITERIA

The application is complete only when all applicable criteria below are satisfied.

## Functional

- [ ] The app launches without requiring internet access.
- [ ] Transactions can be added, edited, viewed, and deleted.
- [ ] Income and expense calculations are correct.
- [ ] All important financial data is persisted in Room.
- [ ] Categories can be managed without corrupting history.
- [ ] Monthly budgets are saved and correctly calculated.
- [ ] Reports use genuine stored transactions.
- [ ] Search and filters work together correctly.
- [ ] Currency amounts are stored without floating-point errors.
- [ ] CSV export works through a user-selected destination.
- [ ] JSON backup and restore are validated and safe.
- [ ] Preferences persist across restarts.
- [ ] The application works without a network connection.

## Engineering

- [ ] Kotlin code is strongly typed and null-safe.
- [ ] The architecture separates presentation, domain, and data responsibilities.
- [ ] Composables do not access Room directly.
- [ ] ViewModels expose appropriate immutable state.
- [ ] Dependencies are pinned and compatible.
- [ ] Room schema export and migration policies are configured.
- [ ] Important financial operations have automated tests.
- [ ] No destructive production migration fallback exists.
- [ ] No unfinished critical implementation remains.
- [ ] No unnecessary internet, storage, or sensitive permissions are requested.

## UI/UX

- [ ] All core screens are implemented.
- [ ] The dashboard uses live database-backed summaries.
- [ ] Navigation and Back behavior work correctly.
- [ ] Light and dark modes work.
- [ ] Forms validate invalid data.
- [ ] Loading, empty, and error states are handled.
- [ ] The interface is responsive on common Android phone sizes.
- [ ] Touch targets, contrast, and content descriptions are accessible.
- [ ] Charts and budget indicators present accurate data.
- [ ] The UI contains no dead buttons or misleading fake financial information.

## Delivery

- [ ] The Android Studio project is complete.
- [ ] The README explains setup and build instructions.
- [ ] Tests have been executed and their results reported honestly.
- [ ] A debug APK is generated if the environment supports it.

## Final Instruction

Begin by inspecting the actual workspace and establishing the compatible build configuration.

Then implement the application in the exact phase order above, validating each layer before building on it.

Make sensible engineering decisions without asking unnecessary questions. Prioritize financial correctness, reliable offline storage, maintainable Kotlin architecture, polished native Android UI, and data safety.

**Your objective is not to produce a prototype or a visual demo. Your objective is to deliver a complete, functional, testable, offline-first Android expense tracker that is ready to build, install, and use.**
