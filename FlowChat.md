---
config:
  layout: dagre
---
flowchart TB
 subgraph Consumer_Flow["Consumer Flow"]
        D1["Post a Job"]
        D["Consumer Dashboard"]
        D2["Job Published"]
        D3["Contractors View Job"]
        D4["Contractors Submit Quotes"]
        D5["Consumer Views Quotes"]
        D6["Job Moves to In Progress"]
        D7["Search More Quotes"]
        D8["More Quotes Arrive"]
        D9["Chat with Contractor"]
        D10["Contractor Marks Work Done"]
        D11["Consumer Confirms Completion"]
        D12["Rate & Review Contractor"]
  end
 subgraph Contractor_Flow["Contractor Flow"]
        E1["Browse & Search Jobs"]
        E["Contractor Dashboard"]
        E2["Filter by Location / Budget / Type"]
        E3["View Job Details"]
        E4["Submit Quote"]
        E5["Waiting for Consumer Response"]
        E6["Job Moves to Active Jobs"]
        E7["Bid Rejected"]
        E8["Job Expires"]
        E9["Messaging with Consumer"]
        E10["Mark Work as Done"]
  end
 subgraph Job_Lifecycle["Job Lifecycle"]
        JL2["Visible to Contractors"]
        JL1["Job Posted"]
        JL3["Quotes Submitted"]
        JL4["Consumer Accepts Quote"]
        JL5["Job In Progress"]
        JL6["Work Completed"]
        JL7["Consumer Confirms Completion"]
        JL8["Job Completed"]
        JL9["Review Added"]
  end
 subgraph Messaging["Real-Time Messaging"]
        M2["Messaging API / WebSocket"]
        M1["Consumer"]
        M3["Contractor"]
  end
 subgraph Admin_Flow["Admin Flow"]
        F1["Manage Users"]
        F["Admin Panel"]
        F2["Approve / Verify Contractors"]
        F3["Monitor Jobs"]
        F4["Active"]
        F5["In Progress"]
        F6["Completed"]
        F7["Disputed"]
        F8["Resolve Disputes"]
        F9["System Reports & Analytics"]
  end
 subgraph Notifications["Notification System"]
        N["Notify Consumer"]
        N1["New Quote"]
        N2["Quote Accepted"]
        N3["New Message"]
        N4["Work Completed"]
        N5["Review Added"]
        N6["Push Notifications"]
  end
    A["Start"] --> B["User Login / Register"]
    B --> C{"User Type?"}
    C --> D & E & F
    D --> D1
    D1 --> D2
    D2 --> D3
    D3 --> D4
    D4 --> D5
    D5 -- Accept --> D6
    D5 -- Reject --> D7
    D5 -- Wait --> D8
    D6 --> D9
    D9 --> D10
    D10 --> D11
    D11 --> D12
    E --> E1
    E1 --> E2
    E2 --> E3
    E3 --> E4
    E4 --> E5
    E5 -- Accepted --> E6
    E5 -- Rejected --> E7
    E5 -- No Response --> E8
    E6 --> E9
    E9 --> E10
    JL1 --> JL2
    JL2 --> JL3
    JL3 --> JL4
    JL4 --> JL5
    JL5 --> JL6
    JL6 --> JL7
    JL7 --> JL8
    JL8 --> JL9
    M1 <--> M2
    M2 <--> M3
    F --> F1 & F3 & F8 & F9
    F1 --> F2
    F3 --> F4 & F5 & F6 & F7
    N1 --> N
    N2 --> N
    N3 --> N
    N4 --> N
    N5 --> N
    N --> N6
