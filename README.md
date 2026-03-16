# BEU Penalty Calculator

This repo reads the old shortlist (`result_students.txt`), uses the validated credit database (`credit_master.txt` and `credit_totals.txt`), fetches:
- old Semester-II BEU HTML result
- new BEU backend result

Then it produces:
- `penalty_calc_output.txt` -> one row per penalized student
- `penalty_audit.txt` -> one row per penalized subject
- `penalty_absent.txt` -> carry-paper absent cases
- `penalty_manual_review.txt` -> doubtful cases
- `penalty_failed.txt` -> fetch/no-result/calculation failures

## Required input files
- `result_students.txt`
- `credit_master.txt`
- `credit_totals.txt`

## Output formats
### penalty_calc_output.txt
`reg_no | branch_code | penalized_subject_codes | subject_names | old_shown_grades | new_shown_grades | should_be_grades | shown_sgpa | corrected_sgpa | shown_cgpa | corrected_cgpa | status | old_result_url | new_result_url`

### penalty_audit.txt
`reg_no | sem | branch_code | subject_code | subject_name | subject_type | credit | old_shown_grade | new_shown_grade | should_be_grade | shown_gp | corrected_gp | delta_points | new_ese | new_ia | new_total | old_result_url | new_result_url`

## Run locally
```bash
npm install
node penalty_calc.js
```

## Resume logic
The script resumes using:
- `penalty_state.json`
- `penalty_seen.txt`

## Notes
- This calculator is configured for current BEU backend Semester-II old regulation result:
  - year = 2025
  - examHeld = November/2025
- It uses the one-step-lower penalty detection logic with grace handling (`*`) and separate theory/practical pass thresholds.
