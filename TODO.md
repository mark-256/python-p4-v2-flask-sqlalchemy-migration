# Flask-Migrate Database Migration Tutorial

## Task Analysis Summary

**Current Repository State:**

- `server/app.py` - Flask application with Flask-Migrate configured
- `server/models.py` - Contains only the `Employee` model
- No migrations directory exists yet
- No instance directory with database file

**Required Steps to Complete:**

### Phase 1: Initial Setup and Migration

1. Set up environment variables (FLASK_APP, FLASK_RUN_PORT)
2. Initialize Flask-Migrate with `flask db init`
3. Create initial migration with `flask db migrate -m "Initial migration."`
4. Apply migration with `flask db upgrade head`
5. Add test data via Flask shell

### Phase 2: Add Department Model (with intentional error)

1. Add Department model with incorrect table name `department` (singular)
2. Generate migration with `flask db migrate -m 'add Department'`
3. Apply migration with `flask db upgrade head`
4. Add test department data

### Phase 3: Fix Table Name (rename department to departments)

1. Change Department model `__tablename__` to `'departments'`
2. Generate migration with `flask db migrate -m "rename department"`
3. **Manually edit** the migration script to use `op.rename_table()` instead of drop/create
4. Apply migration with `flask db upgrade head`

### Phase 4: Rename Column (address to location)

1. Change Department model attribute from `address` to `location`
2. Generate migration with `flask db migrate -m "rename address"`
3. **Manually edit** the migration script to use `op.alter_column()`
4. Apply migration with `flask db upgrade head`

### Phase 5: Demonstrate Downgrade

1. Show how to downgrade to previous version
2. Optionally revert models.py

## Key Concepts to Demonstrate:

- Flask-Migrate auto-generation capabilities
- When manual intervention is required (table/column renaming)
- Using `op.rename_table()` for table renames
- Using `op.alter_column()` for column renames
- Downgrading migrations with `flask db downgrade`

## Final State:

- `server/models.py` with Employee and Department models
- Department model using `__tablename__ = 'departments'` and `location` column
- Complete migration history in `server/migrations/versions/`
