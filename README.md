# Recruitment Task: Virtual Columns in Pandas
**Candidate:** [Your Name]

### Approach & Strategy
This solution is designed with a strong emphasis on **safety, readability, and modularity**. 

Instead of relying on `eval()`—which introduces security risks and is generally an anti-pattern in data engineering pipelines—this solution uses a "Fail Fast" validation strategy combined with Python's built-in `operator` module. 

**Key Design Decisions:**
1. **Strict Validation:** A dedicated helper function (`is_valid_label`) enforces the regex rule `^[a-zA-Z_]+$` to ensure no digits or symbols sneak into the pipeline.
2. **Safe Parsing:** The role string is split and mapped to safe, native mathematical operations, ensuring only the allowed `+`, `-`, and `*` operations are executed.
3. **Fail-Fast Execution:** The main function acts as a pipeline that checks constraints upfront. If any rule is violated (invalid new column, invalid role, or even existing invalid columns in the source DataFrame), it safely and immediately returns an empty DataFrame without raising unhandled exceptions.
4. **Data Integrity:** The mathematical operation is performed on a `.copy()` of the dataframe to prevent `SettingWithCopyWarning` and to preserve the state of the user's original data.
