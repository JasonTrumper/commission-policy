# Commission Policy Flowchart

This document contains a comprehensive visual representation of the Achieve Test Prep Commission Policy for Admissions Representatives.

---

## 1-2: Eligibility & Commission Types

```mermaid
flowchart TB
    subgraph COMMISSION_TYPES ["Commission Types"]
        direction TB
        
        START["Start: Commission Eligibility Check"]
        
        ELIGIBILITY{"Active Employee?"}
        
        ELIGIBLE["Eligible for All Commissions"]
        NOT_ELIGIBLE["Not Eligible for Commissions"]
        
        CASH["Cash Commission: X% on Cash/CC Payments"]
        FINANCED["Financed Commission: X% on Total Financed Amount"]
        
        FINANCED_TIMING["Financed Commission Paid in Thirds:"]
        FIN1["1/3 on Deposit Met Date"]
        FIN2["1/3 at 30 Days After Deposit"]
        FIN3["1/3 at 60 Days After Deposit"]
        
        START --> ELIGIBILITY
        ELIGIBLE --> CASH
        ELIGIBLE --> FINANCED
        FINANCED --> FINANCED_TIMING
        FINANCED_TIMING --> FIN1
        FIN1 --> FIN2
        FIN2 --> FIN3
        
        ELIGIBILITY -->|No| NOT_ELIGIBLE
    end
```

---

## 3: Self-Generated Leads Timeline

```mermaid
flowchart TB
    subgraph SELF_GEN ["Self-Generated Leads"]
        direction TB
        
        LEAD_CREATE["Create New Lead Record in CRM<br/>(Referral or Organization Presentation)"]
        
        LEAD_PROTECT{"Self Gen Lead Date<br/>Populated in CRM?"}
        
        PROTECTED["15 Calendar Days Protected<br/>Lead Ownership Lock"]
        
        ENROLL_15{"Enroll Lead Within<br/>15 Days?"}
        
        BONUS_25["+25% Commission Increase<br/>(125% Total)"]
        
        BONUS_12["+12% Commission Increase<br/>(112% Total)"]
        
        ENROLL_180{"Enroll Lead Within<br/>16-180 Days?"}
        
        NO_BONUS["No Additional Commission"]
        
        OTHER_REP{"Another Rep Enrolls<br/>16-180 Days?"}
        
        REP_12["12% Commission to Original Rep<br/>(100% to Enrolling Rep)"]
        
        NO_ELIGIBLE["No Commission Eligible<br/>(181+ Days)"]
        
        LEAD_CREATE --> LEAD_PROTECT
        LEAD_PROTECT -->|Yes| PROTECTED
        LEAD_PROTECT -->|No| NO_BONUS
        PROTECTED --> ENROLL_15
        ENROLL_15 -->|Yes| BONUS_25
        ENROLL_15 -->|No| ENROLL_180
        ENROLL_180 -->|Yes| BONUS_12
        ENROLL_180 -->|No| NO_ELIGIBLE
        BONUS_12 --> OTHER_REP
        OTHER_REP -->|Yes| REP_12
        OTHER_REP -->|No| NO_ELIGIBLE
    end
```

---

## 4: Commission Earned Conditions

```mermaid
flowchart TB
    subgraph EARNED ["Commission Earned Conditions"]
        direction TB
        
        START_EARNED["Commission Advanced"]
        
        CONDITIONS{"All Conditions Met?"}
        
        FULLY_EARNED["Fully Earned<br/>No Adjustments Applied"]
        
        COND_A["A: All Commission Adjustments Applied (if any)"]
        COND_B["B: Active Employee Status"]
        COND_C["C: All Company Procedures Followed"]
        
        NOT_EARNED["Not Yet Earned<br/>Subject to Adjustments"]
        
        PAYROLL_REDUCTION["Possible Payroll Reduction<br/>(If Procedures Not Followed)"]
        
        START_EARNED --> CONDITIONS
        CONDITIONS -->|Yes| FULLY_EARNED
        CONDITIONS -->|No| NOT_EARNED
        
        NOT_EARNED --> COND_A
        NOT_EARNED --> COND_B
        NOT_EARNED --> COND_C
        COND_C --> PAYROLL_REDUCTION
    end
```

---

## 5.1: Withdrawal Requests (72 Hours)

```mermaid
flowchart TB
    subgraph WITHDRAWAL ["5.1: Withdrawal Requests (72 Hours)"]
        direction TB
        
        WITHDRAWAL_START["Customer Requests Withdrawal<br/>(Within 72 Hours of Enrollment)"]
        
        FROZEN{"Account in Freeze/Reduced Payment<br/>or Delayed Start?"}
        
        PAUSE["72-Hour Clock Pauses<br/>Resumes When Account Off Hold"]
        
        WITHDRAWAL_HOLD["72-Hour Clock Resumes"]
        
        CS_SAVE{"Retention/CS Department<br/>Save Customer?"}
        
        CS_SAVED["Commission Unchanged<br/>(Unless Course Package Modified)"]
        
        PACKAGE_CHANGE{"Course Package Modified?"}
        
        RECALC_PACKAGE["Commission Recalculated<br/>(Based on Updated Package)"]
        
        OVER_UNDER["Overpayment Deducted<br/>OR Underpayment Added"]
        
        REFUND_ISSUED["Customer Issued Refund"]
        
        RECALC_REFUND["Commission Recalculated<br/>(Collected Amount - Refund)"]
        
        OVERPAY_DEDUCT["Overpayment Deducted<br/>on Following Paycheck"]
        
        POST_WITHDRAWAL{"Payments After Withdrawal?"}
        
        NO_COMMISSION["No Commission on<br/>Subsequent Payments"]
        
        WITHDRAWAL_START --> FROZEN
        FROZEN -->|Yes| PAUSE
        PAUSE --> WITHDRAWAL_HOLD
        FROZEN -->|No| CS_SAVE
        WITHDRAWAL_HOLD --> CS_SAVE
        CS_SAVE -->|Yes| CS_SAVED
        CS_SAVED --> PACKAGE_CHANGE
        PACKAGE_CHANGE -->|Yes| RECALC_PACKAGE
        PACKAGE_CHANGE -->|No| OVER_UNDER
        CS_SAVE -->|No| REFUND_ISSUED
        REFUND_ISSUED --> RECALC_REFUND
        RECALC_REFUND --> OVERPAY_DEDUCT
        OVERPAY_DEDUCT --> POST_WITHDRAWAL
        POST_WITHDRAWAL -->|Yes| NO_COMMISSION
    end
```

---

## 5.2: Deposit Payment Reversals

```mermaid
flowchart TB
    subgraph REVERSAL ["5.2: Deposit Payment Reversals"]
        direction TB
        
        REVERSAL_START["Customer Deposit Reversed<br/>(Within 30 Days of Dep Met Date)"]
        
        REVERSAL_TYPE{"Type of Reversal"}
        
        NSF["Insufficient Funds<br/>Stop Payment on Check/ACH"]
        
        CHARGEBACK["Credit Card Chargeback"]
        
        WITHIN_45{"Within 45 Days of<br/>Deposit Met Date?"}
        
        ORIGINAL_SALE["Original Sale Invalidated"]
        
        COMM_REMOVED["Commission Advance Removed<br/>(Deducted on Following Paycheck)"]
        
        CHARGEBACK_REVERSED{"Chargeback Reversed?"}
        
        DEP_UPDATED["Deposit Met Date Updated<br/>(To Reversal Date)"]
        
        COMM_REINSTATED["Commission Reinstated<br/>(Added to Following Paycheck)"]
        
        REVERSAL_START --> REVERSAL_TYPE
        REVERSAL_TYPE --> NSF
        REVERSAL_TYPE --> CHARGEBACK
        NSF --> WITHIN_45
        CHARGEBACK --> WITHIN_45
        WITHIN_45 -->|Yes| ORIGINAL_SALE
        ORIGINAL_SALE --> COMM_REMOVED
        WITHIN_45 -->|No| CHECK_FULL["Check: Full Commission Paid?<br/>(Within 30 Days)"]
        CHECK_FULL -->|Yes| NO_CHANGE["No Commission Change"]
        CHECK_FULL -->|No| COMM_REMOVED
        CHARGEBACK --> CHARGEBACK_REVERSED
        CHARGEBACK_REVERSED -->|Yes| DEP_UPDATED
        DEP_UPDATED --> COMM_REINSTATED
        CHARGEBACK_REVERSED -->|No| COMM_REMOVED
    end
```

---

## 5.3: PIF Installment Payment Reversals

```mermaid
flowchart TB
    subgraph PIF_REVERSAL ["5.3: PIF Installment Payment Reversals"]
        direction TB
        
        PIF_START["PIF Installment Payment Reversed<br/>(Within 30 Days of Receipt)"]
        
        PIF_REV_TYPE{"Type of Reversal"}
        
        PIF_NSF["Insufficient Funds<br/>Stop Payment on Check/ACH"]
        
        PIF_CHARGEBACK["Credit Card Chargeback"]
        
        PIF_RECALC["Commission Recalculated<br/>(Excluding Reversed Amount)"]
        
        PIF_OVERPAY["Overpayment Deducted<br/>(On Following Paycheck)"]
        
        PIF_CHARGEBACK_REV{"Chargeback Reversed?"}
        
        PIF_DEP_UPDATED["Deposit Met Date Updated<br/>(To Reversal Date)"]
        
        PIF_COMM_RESTORED["Commission Restored<br/>(Prior Deductions Added Back)"]
        
        PIF_START --> PIF_REV_TYPE
        PIF_REV_TYPE --> PIF_NSF
        PIF_REV_TYPE --> PIF_CHARGEBACK
        PIF_NSF --> PIF_RECALC
        PIF_CHARGEBACK --> PIF_RECALC
        PIF_RECALC --> PIF_OVERPAY
        PIF_CHARGEBACK --> PIF_CHARGEBACK_REV
        PIF_CHARGEBACK_REV -->|Yes| PIF_DEP_UPDATED
        PIF_DEP_UPDATED --> PIF_COMM_RESTORED
        PIF_CHARGEBACK_REV -->|No| PIF_OVERPAY
    end
```

---

## 5.4: Account Status Changes

```mermaid
flowchart TB
    subgraph STATUS_CHANGE ["5.4: Account Status Changes"]
        direction TB
        
        STATUS_START["Account Status Changes to:<br/>Loan/PIF Payment Freeze<br/>Loan Reduced Payment<br/>Delayed Start"]
        
        STATUS_WITHIN{"Within 72 Hours of<br/>Enrollment Agreement?"}
        
        STATUS_RECALC["Commission Recalculated<br/>(Based on Collected Amount Only)"]
        
        NO_FINANCED["Financed Commission Not Advanced"]
        
        STATUS_DEDUCT["Overpayment Deducted<br/>(On Following Paycheck)"]
        
        OFF_HOLD{"Account Status Taken Off Hold"}
        
        OFF_HOLD_TIMING{"Within 180 Days<br/>of Original Request?"}
        
        ACTIVE_EMP{"Still Active Employee?"}
        
        STATUS_RESTORED["Prior Deductions Restored<br/>(Subject to Program Modifications)"]
        
        FINANCED_ADVANCED["Financed Commission Advanced<br/>(Per Payment Schedule)"]
        
        STATUS_START --> STATUS_WITHIN
        STATUS_WITHIN -->|Yes| STATUS_RECALC
        STATUS_RECALC --> NO_FINANCED
        NO_FINANCED --> STATUS_DEDUCT
        STATUS_DEDUCT --> OFF_HOLD
        OFF_HOLD --> OFF_HOLD_TIMING
        OFF_HOLD_TIMING -->|Yes| ACTIVE_EMP
        ACTIVE_EMP -->|Yes| STATUS_RESTORED
        STATUS_RESTORED --> FINANCED_ADVANCED
        OFF_HOLD_TIMING -->|No| NO_RESTORE["No Restoration<br/>(180+ Days Elapsed)"]
        STATUS_WITHIN -->|No| NO_RECALC["No Commission Recalculation"]
    end
```

---

## 5.5: Program Modifications - Dropping Courses

```mermaid
flowchart TB
    subgraph DROP_COURSES ["5.5: Program Modifications - Dropping Courses"]
        direction TB
        
        DROP_START["Course Package Reduced"]
        
        DROP_REASON{"Reason for Reduction"}
        
        DROP_72["Within 72 Hours of<br/>Enrollment Agreement"]
        
        DROP_TRANSCRIPT["Transcript Review<br/>or Degree Planning Report"]
        
        DROP_PAYMENT["Payment Method Change:<br/>Financed → PIF within 60 Days"]
        
        DROP_RECALC["Commission Recalculated<br/>(Based on New Total Amount)"]
        
        DROP_DEDUCT["Overpayment Deducted<br/>(From Following Paycheck)"]
        
        DROP_START --> DROP_REASON
        DROP_REASON --> DROP_72
        DROP_REASON --> DROP_TRANSCRIPT
        DROP_TRANSCRIPT --> DROP_PAYMENT
        DROP_PAYMENT --> DROP_RECALC
        DROP_72 --> DROP_RECALC
        DROP_RECALC --> DROP_DEDUCT
    end
```

---

## 5.6: Program Modifications - Adding Courses

```mermaid
flowchart TB
    subgraph ADD_COURSES ["5.6: Program Modifications - Adding Courses"]
        direction TB
        
        ADD_START["Course Package Increased"]
        
        ADD_REASON{"Reason for Increase"}
        
        ADD_72["Within 72 Hours of<br/>Enrollment Agreement"]
        
        ADD_TRANSCRIPT["Transcript Review<br/>or Degree Planning Report"]
        
        ADD_PAYMENT["Payment Method Change:<br/>Financed → PIF within 60 Days"]
        
        ADD_RECALC["Commission Recalculated<br/>(Based on New Total Amount)"]
        
        ADD_ADD["Commission Added<br/>(To Following Paycheck)"]
        
        ADD_START --> ADD_REASON
        ADD_REASON --> ADD_72
        ADD_REASON --> ADD_TRANSCRIPT
        ADD_TRANSCRIPT --> ADD_PAYMENT
        ADD_PAYMENT --> ADD_RECALC
        ADD_72 --> ADD_RECALC
        ADD_RECALC --> ADD_ADD
    end
```

---

## 5.7: Payment Method Changes

```mermaid
flowchart TB
    subgraph PAYMENT_METHOD ["5.7: Payment Method Changes"]
        direction TB
        
        PM_START["Payment Method Changed in CRM"]
        
        PM_FIN_TO_PIF{"Financed Option → PIF Option"}
        
        PM_PIF_TO_FIN{"PIF Option → Financed Option"}
        
        PM_TIMING_60{"Within 60 Days of<br/>Enrollment Agreement?"}
        
        PM_RECALC_FP["Recalculate at PIF<br/>Commission Rate"]
        
        PM_ADJUST_FP["Underpayment Added<br/>OR Overpayment Deducted"]
        
        PM_RECALC_FIN["Recalculate at Financed Rate<br/>(Minus PIF Payments Made)"]
        
        PM_EXCLUDE_PIF["Exclude PIF Installment Payments<br/>Made Before Change"]
        
        PM_ADJUST_FIN["Underpayment Added<br/>OR Overpayment Deducted"]
        
        PM_NO_RECALC["No Recalculation Required"]
        
        PM_START --> PM_FIN_TO_PIF
        PM_FIN_TO_PIF --> PM_TIMING_60
        PM_TIMING_60 -->|Yes| PM_RECALC_FP
        PM_RECALC_FP --> PM_ADJUST_FP
        PM_TIMING_60 -->|No| PM_NO_RECALC
        PM_START --> PM_PIF_TO_FIN
        PM_PIF_TO_FIN --> PM_RECALC_FIN
        PM_RECALC_FIN --> PM_EXCLUDE_PIF
        PM_EXCLUDE_PIF --> PM_ADJUST_FIN
    end
```

---

## 5.8: Financing Option with Financial Partner

```mermaid
flowchart TB
    subgraph FIN_PARTNER ["5.8: Financing Option with Financial Partner"]
        direction TB
        
        FIN_START["Customer Eligible for and Selects<br/>Financing Through Financial Partner"]
        
        FIN_CS_CREATE["Customer Success Team Creates<br/>New Quote"]
        
        FIN_ORIGINAL["Original Quote Remains Intact"]
        
        FIN_ORIGINAL_RATE["Sales Commission Based on<br/>Original Quote & Payment Method"]
        
        FIN_NO_RECALC["Commission NOT Recalculated"]
        
        FIN_START --> FIN_CS_CREATE
        FIN_CS_CREATE --> FIN_ORIGINAL
        FIN_ORIGINAL --> FIN_ORIGINAL_RATE
        FIN_ORIGINAL_RATE --> FIN_NO_RECALC
    end
```

---

## 5.9: Good Faith Violations

```mermaid
flowchart TB
    subgraph GOOD_FAITH ["5.9: Good Faith & Fair Dealing Violations"]
        direction TB
        
        VIOLATION_START["Management Investigation Complete"]
        
        VIOLATION_FOUND{"Violation Confirmed?"}
        
        FORFEIT["Commission Forfeited<br/>(Related Sale)"]
        
        VIOLATION_TYPES["Types of Violations:"]
        
        MISLEADING["Misleading Customer<br/>(Verbal/Written)"]
        
        OMISSION["Omission of Information<br/>(Should Have Been Relayed)"]
        
        PERSONAL_GAIN["Personal Gain at Detriment<br/>of Customer/Company"]
        
        DISCIPLINARY["Disciplinary Action:<br/>Warning → Probation → Termination"]
        
        VIOLATION_START --> VIOLATION_FOUND
        VIOLATION_FOUND -->|Yes| FORFEIT
        FORFEIT --> VIOLATION_TYPES
        VIOLATION_TYPES --> MISLEADING
        VIOLATION_TYPES --> OMISSION
        VIOLATION_TYPES --> PERSONAL_GAIN
        MISLEADING --> DISCIPLINARY
        OMISSION --> DISCIPLINARY
        PERSONAL_GAIN --> DISCIPLINARY
        VIOLATION_FOUND -->|No| NO_ACTION["No Commission Impact"]
    end
```

---

## 6: Draw Against Future Commissions

```mermaid
flowchart TB
    subgraph DRAW ["6: Draw Against Future Commissions"]
        direction TB
        
        DRAW_START["Employee Receives Draw<br/>(Payroll Advance Against Future Commissions)"]
        
        DRAW_DEFINITION["Draw = Advance Against Future Commissions<br/>(Considered a Loan)"]
        
        REPPAY_OBLIGATION["Repay via Earned Commissions<br/>OR Other Means"]
        
        EMPLOYMENT_END["Employment Ends<br/>(Voluntary or Involuntary)"]
        
        COMM_COVER{"Commissions Earned Cover Draw?"}
        
        COMM_GREATER["Surplus: Employee Keeps Difference"]
        
        COMM_LESS["Deficit: Employee Responsible<br/>for Remaining Balance"]
        
        FINAL_PAYCHECK["Final Paycheck Applied<br/>(Base, Vacation, Commissions, Bonus)"]
        
        REMAINING_BALANCE{"Any Balance Remaining?"}
        
        DEMAND_NOTICE["Employer Demands Repayment"]
        
        EMPLOYEE_REPAY["Employee Repays Balance"]
        
        DRAW_CLEAR["Draw Balance Cleared"]
        
        DRAW_START --> DRAW_DEFINITION
        DRAW_DEFINITION --> REPPAY_OBLIGATION
        REPPAY_OBLIGATION --> EMPLOYMENT_END
        EMPLOYMENT_END --> COMM_COVER
        COMM_COVER -->|Yes| COMM_GREATER
        COMM_COVER -->|No| COMM_LESS
        COMM_LESS --> FINAL_PAYCHECK
        FINAL_PAYCHECK --> REMAINING_BALANCE
        REMAINING_BALANCE -->|Yes| DEMAND_NOTICE
        DEMAND_NOTICE --> EMPLOYEE_REPAY
        REMAINING_BALANCE -->|No| DRAW_CLEAR
    end
```

---

## 7: Booker Commissions

```mermaid
flowchart TB
    subgraph BOOKER ["7: Booker Commissions"]
        direction TB
        
        BOOKER_START["Schedule Appointment for<br/>Another Admissions Rep"]
        
        APPT_HELD{"Appointment Actually Held?"}
        
        SHOW_STATUS["'Show/No Show' Status = 'Show'"]
        
        SHOW_NO_SHOW["'Show' = Commission Earned<br/>'No Show' = No Commission"]
        
        LEAD_STATUS{"Lead Status at Time of Booking"}
        
        COLD_NEVER["Cold – Never Spoke To: $15.20"]
        COLD_FUTURE["Cold Future: $15.20"]
        DEAD["Dead: $15.20"]
        DROPPED_BALL["Dropped Ball: $12.54"]
        GETTING_COLD["Getting Cold: $10.64"]
        IN_CLOSING["In Closing: $3.80"]
        IN_CLOSING_LT["In Closing – Long Term Close: $3.80"]
        IN_PROGRESS["In Progress: $3.80"]
        IN_PROGRESS_HOT["In Progress – Hot: $3.80"]
        NEW_LEAD["New Lead: $10.64"]
        PRE_LEAD["Pre-Lead (Default, Pre-License, Referred): $11.40"]
        ENROLLED["Enrolled: $10.64"]
        
        PHONE_APP{"Meeting Via = 'Phone'?"}
        
        PHONE_RATE["Phone Appointment Rate: $3.04"]
        
        PHONE_OVERRIDE["Phone Rate Overrides<br/>All Other Rates"]
        
        RESCHEDULE{"Reschedule of No Show Appointment?"}
        
        ORIGINAL_BOOKER{"Original Booked Within 76<br/>Weekday Hours?"}
        
        ORIGINAL_KEEPS["Original Booker Keeps Commission"]
        
        RESCHEDULE_KEEPS["Rescheduler Gets Commission"]
        
        BOOKER_START --> APPT_HELD
        APPT_HELD --> SHOW_STATUS
        SHOW_STATUS --> SHOW_NO_SHOW
        SHOW_NO_SHOW -->|Show| LEAD_STATUS
        LEAD_STATUS --> COLD_NEVER
        LEAD_STATUS --> COLD_FUTURE
        LEAD_STATUS --> DEAD
        LEAD_STATUS --> DROPPED_BALL
        LEAD_STATUS --> GETTING_COLD
        LEAD_STATUS --> IN_CLOSING
        LEAD_STATUS --> IN_CLOSING_LT
        LEAD_STATUS --> IN_PROGRESS
        LEAD_STATUS --> IN_PROGRESS_HOT
        LEAD_STATUS --> NEW_LEAD
        LEAD_STATUS --> PRE_LEAD
        LEAD_STATUS --> ENROLLED
        
        LEAD_STATUS --> PHONE_APP
        PHONE_APP -->|Yes| PHONE_RATE
        PHONE_RATE --> PHONE_OVERRIDE
        
        APPT_HELD -->|No Show| RESCHEDULE
        RESCHEDULE --> ORIGINAL_BOOKER
        ORIGINAL_BOOKER -->|Yes| ORIGINAL_KEEPS
        ORIGINAL_BOOKER -->|No| RESCHEDULE_KEEPS
    end
```

---

## 8: Payment of Commission

```mermaid
flowchart TB
    subgraph PAYMENT ["8: Payment of Commission"]
        direction TB
        
        PAY_START["Commission Paid in Biweekly Paycheck"]
        
        PAY_TRIGGER{"Payment Trigger Events"}
        
        TRIGGER_1["1. Deposit Payments Received & Cleared"]
        TRIGGER_2["2. PIF Installment Payments Received & Cleared"]
        TRIGGER_3["3. Financed Commission Thirds:<br/>- 1/3: Deposit Met Date<br/>- 1/3: 30 Days After<br/>- 1/3: 60 Days After"]
        
        PAY_ADVANCE["Commission Advanced at Trigger"]
        
        PAY_NOTICE["NOTIFICATION: Advanced ≠ Earned<br/>(See Section 4: Earned Conditions)"]
        
        PAY_ADJUST["Subject to Future Adjustments<br/>(Sections 5.1-5.8)"]
        
        PAY_START --> PAY_TRIGGER
        PAY_TRIGGER --> TRIGGER_1
        PAY_TRIGGER --> TRIGGER_2
        PAY_TRIGGER --> TRIGGER_3
        TRIGGER_1 --> PAY_ADVANCE
        TRIGGER_2 --> PAY_ADVANCE
        TRIGGER_3 --> PAY_ADVANCE
        PAY_ADVANCE --> PAY_NOTICE
        PAY_NOTICE --> PAY_ADJUST
    end
```

---

## 9: Sales Commission Sharing

```mermaid
flowchart TB
    subgraph SHARING ["9: Sales Commission Sharing"]
        direction TB
        
        SHARE_START["Another Rep Helps Close Enrollment"]
        
        SHARE_TYPE{"Sharing Scenario"}
        
        SHARE_DROPPED["Lead Record Reached<br/>'Dropped Ball' Status"]
        
        SHARE_HELPED["Other Rep Helps Close Enrollment"]
        
        SHARE_SPLIT["50% of Sales Commission<br/>to Helping Rep"]
        
        SHARE_REQUEST["Customer Requests Different Rep"]
        
        SHARE_NEW_CLOSE["New Rep Closes Enrollment"]
        
        SHARE_DISCRETION["Management Discretion<br/>on Split %"]
        
        SHARE_START --> SHARE_TYPE
        SHARE_TYPE --> SHARE_DROPPED
        SHARE_DROPPED --> SHARE_HELPED
        SHARE_HELPED --> SHARE_SPLIT
        
        SHARE_TYPE --> SHARE_REQUEST
        SHARE_REQUEST --> SHARE_NEW_CLOSE
        SHARE_NEW_CLOSE --> SHARE_DISCRETION
    end
```

---

## 10: Entire Policy & Legal

```mermaid
flowchart TB
    subgraph LEGAL ["10: Entire Policy & Legal"]
        direction TB
        
        POLICY_COMPLETE["Entire Policy Document"]
        
        NO_OTHER["No Other Representations/Promises<br/>(Not in This Policy)"]
        
        NOT_GUARANTEE["NOT a Guarantee of<br/>Continuous Employment"]
        
        AT_WILL["Employee Remains At-Will<br/>(Unless State Law Says Otherwise)"]
        
        POLICY_AMEND{"Policy Changes"]
        
        WRITTEN_ONLY["Written Agreement Required<br/>(To Amend/Modify/Waive)"]
        
        COMPANY_RIGHT["Company May Change/Terminate<br/>At Any Time"]
        
        NOTICE_REQUIRED["Advance Written Notice<br/>Provided to Employees"]
        
        GOVERNING_LAW{"Unless Prohibited by Law"]
        
        NJ_LAW["Laws of New Jersey Govern"]
        
        JURISDICTION["Morris County, NJ Courts<br/>(Personal Jurisdiction & Venue)"]
        
        DISPUTE_RESOLUTION{"Dispute Resolution"]
        
        INDIVIDUAL_ONLY["Individual Basis Only<br/>(No Class Actions)"]
        
        NO_PGA["No Private Attorney General Actions<br/>(Unless Agreed in Writing)"]
        
        POLICY_COMPLETE --> NO_OTHER
        NO_OTHER --> NOT_GUARANTEE
        NOT_GUARANTEE --> AT_WILL
        AT_WILL --> POLICY_AMEND
        POLICY_AMEND --> WRITTEN_ONLY
        WRITTEN_ONLY --> COMPANY_RIGHT
        COMPANY_RIGHT --> NOTICE_REQUIRED
        NOTICE_REQUIRED --> GOVERNING_LAW
        GOVERNING_LAW --> NJ_LAW
        NJ_LAW --> JURISDICTION
        JURISDICTION --> DISPUTE_RESOLUTION
        DISPUTE_RESOLUTION --> INDIVIDUAL_ONLY
        INDIVIDUAL_ONLY --> NO_PGA
    end
```

---

## Salesforce Automation Rules

```mermaid
flowchart TB
    subgraph SALESFORCE ["Salesforce Commission Automation"]
        direction TB
        
        SF_START["Quote in Salesforce"]
        
        SF_RULE_1{"RULE 1: All Criteria Met?"]
        
        SF_COND_A["Accounting Active OR CT Active = Checked"]
        SF_COND_B["Dep Met = Checked AND Dep Met Date Populated"]
        SF_COND_C["Payment Status ≠ 'Withdraw - 72 hours'"]
        
        SF_ENABLE["Commission Automation ENABLED"]
        
        SF_DISABLE{"RULE 2: Automation Disabled?"]
        
        SF_FULL_PAID["Full Commission Potential<br/>Already Paid"]
        
        SF_30_DAYS{">30 Days After<br/>Deposit Met Date?"}
        
        SF_DISABLED["Commission Automation DISABLED<br/>(No Future Adjustments)"]
        
        SF_START --> SF_RULE_1
        SF_RULE_1 --> SF_COND_A
        SF_RULE_1 --> SF_COND_B
        SF_RULE_1 --> SF_COND_C
        SF_COND_A --> SF_ENABLE
        SF_COND_B --> SF_ENABLE
        SF_COND_C --> SF_ENABLE
        SF_ENABLE --> SF_DISABLE
        SF_DISABLE --> SF_FULL_PAID
        SF_DISABLE --> SF_30_DAYS
        SF_30_DAYS -->|Yes| SF_DISABLED
        SF_30_DAYS -->|No| SF_ENABLE
    end
```

---

## Commission Policy Overview (Summary Diagram)

```mermaid
flowchart TB
    subgraph OVERVIEW ["Commission Policy Overview"]
        direction TB
        
        START["Commission Policy<br/>For Admissions Reps"]
        
        ELIGIBILITY["1. Active Employee Required"]
        
        COMMISSION_TYPES["2. Commission Types:<br/>- Cash: X% on Cash/CC<br/>- Financed: X% in Thirds"]
        
        SELF_GEN["3. Self-Generated Leads:<br/>- 15 days protected<br/>- 16-180 days: +12%<br/>- 181+ days: 0%"]
        
        EARNED["4. Earned When:<br/>- Adjustments Applied<br/>- Active Employee<br/>- Procedures Followed"]
        
        ADJUSTMENTS["5. Adjustment Scenarios:<br/>- Withdrawals<br/>- Payment Reversals<br/>- Program Changes<br/>- Payment Method Changes<br/>- Good Faith Violations"]
        
        DRAW["6. Draw Repayment:<br/>- Loan Against Future Commissions<br/>- Repay at Termination"]
        
        BOOKER["7. Booker Commissions:<br/>- Schedule Appointments<br/>- Rates by Lead Status<br/>- Phone = $3.04 Override"]
        
        PAYMENT["8. Payment Timing:<br/>- Biweekly Paychecks<br/>- Triggered by Payments"]
        
        SHARING["9. Commission Sharing:<br/>- Dropped Ball Help: 50%<br/>- Customer Request: Discretionary"]
        
        LEGAL["10. Legal:<br/>- At-Will Employment<br/>- NJ Law Governs<br/>- Individual Dispute Resolution"]
        
        START --> ELIGIBILITY
        ELIGIBILITY --> COMMISSION_TYPES
        COMMISSION_TYPES --> SELF_GEN
        SELF_GEN --> EARNED
        EARNED --> ADJUSTMENTS
        ADJUSTMENTS --> DRAW
        DRAW --> BOOKER
        BOOKER --> PAYMENT
        PAYMENT --> SHARING
        SHARING --> LEGAL
    end
```

---

## Document Information

| Item | Value |
|------|-------|
| Policy Version | 10.27.2020 |
| Company | Gotham City Ventures LLC<br/>East Coast Test Prep LLC d/b/a Achieve Test Prep<br/>Achieve-it Management Corp |
| Document Type | Commission Policy Flowchart |
| Created From | Commission Policy.txt<br/>Commission Logic.txt |
