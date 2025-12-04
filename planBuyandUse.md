flowchart TD

%% ===========================
%% ENTRY
%% ===========================
A[Contractor Dashboard] --> B[Subscription & Billing]

B --> C{What do you want to do?}
C --> D[View Plans]
C --> E[Change / Upgrade Plan]
C --> F[Purchase Extra Credits]

%% ===========================
%% VIEW PLAN DETAILS
%% ===========================
subgraph PLAN_DETAILS[Plan Options]
    D --> P1[Basic Plan
    - Limited applications
    - No job alerts
    - Pay-per-application]

    D --> P2[Premium Plan
    - Verified badge
    - Highlighted listing
    - Free monthly credits
    - All Pro features]

    D --> P3[Pro Plan
    - Unlimited applications
    - Instant job alerts
    - Priority in search
    - Lower lead cost]
end

%% ===========================
%% CHANGE PLAN STAGE
%% ===========================
subgraph PLAN_CHANGE[Plan Change Process]
    E --> S1{Select New Plan}

    S1 -->|Basic| B1[Switch to Basic
    - Remove premium features
    - Disable job alerts
    - Applications limited]

    S1 -->|Premium| B2[Switch to Premium
    - Add verified badge
    - Add monthly credits
    - Highlight listings]

    S1 -->|Pro| B3[Switch to Pro
    - Unlimited applications
    - Instant notifications
    - Lower cost per job]
end

%% ===========================
%% CREDIT PURCHASE STAGE
%% ===========================
subgraph CREDITS[Credits System]
    F --> CR1[Select Credit Package]
    CR1 --> CR2[Process Payment]
    CR2 --> CR3[Increase Credit Balance]
end

%% ===========================
%% ADMIN OVERRIDE
%% ===========================
subgraph ADMIN[Admin Control]
    A --> AD1[Admin Can Change Contractor Plan]
    AD1 --> AD2[Plans Updated Dynamically]
end

%% ===========================
%% FINALIZATION
%% ===========================
B1 --> Z[Subscription Updated]
B2 --> Z
B3 --> Z
CR3 --> Z
AD2 --> Z

Z --> END[End]
