```

flowchart TB
%% ===========================
%% ENTRY
%% ===========================
A[Start] --> B[User Login / Register]

B --> C{User Type?}
C --> D[Consumer Dashboard]
C --> E[Contractor Dashboard]
C --> F[Admin Panel]

%% ===========================
%% CONSUMER FLOW
%% ===========================
subgraph Consumer_Flow["Consumer Flow"]
    D --> D1[Post a Job]
    D1 --> D2[Job Published]
    D2 --> D3[Contractors View Job]
    D3 --> D4[Contractors Submit Quotes]
    D4 --> D5[Consumer Views Quotes]

    D5 -- Accept --> D6[Job Moves to In Progress]
    D5 -- Reject --> D7[Search More Quotes]
    D5 -- Wait --> D8[More Quotes Arrive]

    D6 --> D9[Chat with Contractor]
    D9 --> D10[Contractor Marks Work Done]
    D10 --> D11[Consumer Confirms Completion]
    D11 --> D12[Rate & Review Contractor]
end

%% ===========================
%% CONTRACTOR FLOW
%% ===========================
subgraph Contractor_Flow["Contractor Job Flow"]
    E --> E1[Browse & Search Jobs]
    E1 --> E2[Filter by Location / Budget / Type]
    E2 --> E3[View Job Details]
    E3 --> E4[Submit Quote]
    E4 --> E5[Waiting for Consumer Response]

    E5 -- Accepted --> E6[Job Moves to Active Jobs]
    E5 -- Rejected --> E7[Bid Rejected]
    E5 -- No Response --> E8[Job Expires]

    E6 --> E9[Messaging with Consumer]
    E9 --> E10[Mark Work as Done]
end

%% ===========================
%% CONTRACTOR SUBSCRIPTION & BILLING
%% ===========================
subgraph Subscription["Subscription & Billing"]
    E --> SB[Subscription & Billing]
    SB --> SBQ{What do you want to do?}

    SBQ --> VP[View Plans]
    SBQ --> CP[Change / Upgrade Plan]
    SBQ --> PC[Purchase Extra Credits]

    %% Plan Details
    subgraph PLAN_DETAILS["Plan Options"]
        VP --> P1[Basic Plan\n- Limited applications\n- No job alerts\n- Pay-per-application]
        VP --> P2[Premium Plan\n- Verified badge\n- Highlighted listings\n- Monthly credits\n- All Pro features]
        VP --> P3[Pro Plan\n- Unlimited applications\n- Instant alerts\n- Priority search\n- Lower lead cost]
    end

    %% Change Plan
    subgraph PLAN_CHANGE["Plan Change Process"]
        CP --> SP{Select New Plan}

        SP -->|Basic| B1[Switch to Basic\n- Remove premium features\n- Disable alerts\n- Limited applications]
        SP -->|Premium| B2[Switch to Premium\n- Verified badge\n- Monthly credits\n- Highlight listings]
        SP -->|Pro| B3[Switch to Pro\n- Unlimited applications\n- Instant alerts\n- Lower cost]
    end

    %% Credit Purchase
    subgraph CREDITS["Credits System"]
        PC --> CR1[Select Credit Package]
        CR1 --> CR2[Process Payment]
        CR2 --> CR3[Increase Credit Balance]
    end
end

%% ===========================
%% JOB LIFECYCLE
%% ===========================
subgraph Job_Lifecycle["Job Lifecycle"]
    JL1[Job Posted] --> JL2[Visible to Contractors]
    JL2 --> JL3[Quotes Submitted]
    JL3 --> JL4[Consumer Accepts Quote]
    JL4 --> JL5[Job In Progress]
    JL5 --> JL6[Work Completed]
    JL6 --> JL7[Consumer Confirms Completion]
    JL7 --> JL8[Job Completed]
    JL8 --> JL9[Review Added]
end

%% ===========================
%% REAL-TIME MESSAGING
%% ===========================
subgraph Messaging["Real-Time Messaging"]
    M1[Consumer] <--> M2[Messaging API / WebSocket]
    M2 <--> M3[Contractor]
end

%% ===========================
%% ADMIN FLOW
%% ===========================
subgraph Admin_Flow["Admin Panel"]
    F --> F1[Manage Users]
    F1 --> F2[Approve / Verify Contractors]

    F --> F3[Monitor Jobs]
    F3 --> F4[Active Jobs]
    F3 --> F5[In Progress Jobs]
    F3 --> F6[Completed Jobs]
    F3 --> F7[Disputed Jobs]

    F --> F8[Resolve Disputes]

    F --> F9[System Reports & Analytics]

    %% Admin Subscription Override
    F --> AD1[Admin Can Change Contractor Plan]
    AD1 --> AD2[Plans Updated Dynamically]
end

%% ===========================
%% NOTIFICATION SYSTEM
%% ===========================
subgraph Notifications["Notification System"]
    N1[New Quote] --> N[Notify Consumer]
    N2[Quote Accepted] --> N
    N3[New Message] --> N
    N4[Work Completed] --> N
    N5[Review Added] --> N
    N --> N6[Push Notifications]
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
``
