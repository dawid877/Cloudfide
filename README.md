# Recruitment Task: Virtual Columns in Pandas
**Candidate:** [Dawid Grzesiak]

**Key Design Decisions:**
1. **Strict Validation:** A dedicated helper function (`is_valid_label`) enforces the regex rule `^[a-zA-Z_]+$` to ensure no digits or symbols sneak into the pipeline.
2. **Safe Parsing:** The role string is split and mapped to safe, native mathematical operations, ensuring only the allowed `+`, `-`, and `*` operations are executed.
3. **Fail-Fast Execution:** The main function acts as a pipeline that checks constraints upfront. If any rule is violated (invalid new column, invalid role, or even existing invalid columns in the source DataFrame), it safely and immediately returns an empty DataFrame without raising unhandled exceptions.
4. **Data Integrity:** The mathematical operation is performed on a `.copy()` in order to preserve the state of the user's original data.
