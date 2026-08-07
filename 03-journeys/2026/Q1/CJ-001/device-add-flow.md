flowchart TD

    A([Start]) --> B[Open Device Manager]
    B --> C[Click Add Device]
    C --> D[Select Add Manually]
    D --> E[Select Device Type: Camera]

    E --> F{Select Identification Method}

%% ----------------------------
%% Network Address Flow
%% ----------------------------

    F -->|Network Address| G[Enter Network Address<br/>IPv4 / IPv6 / Hostname<br/>Port, Protocol,<br/>Username, Password]
    G --> H[Click Next]
    H --> I[Select Device Node]

    I --> J{Node Type}

    %% ONVIF
    J -->|ONVIF Node| K[Test Connection]
    K --> L[Validate Reachability<br/>Authentication<br/>ONVIF Compatibility]
    L --> M{Validation Successful?}

    M -->|No| N[Display Error<br/>Update Details & Retry]
    N --> G

    M -->|Yes| O[Proceed to Review]

    %% CI
    J -->|CI Node| P[Send Onboarding Configuration]
    P --> Q[Device Connects to CI Node]
    Q --> R{Connection Successful?}

    R -->|No| S[Display Error<br/>Correct Details & Retry]
    S --> G

    R -->|Yes| O

%% ----------------------------
%% MAC Address Flow
%% ----------------------------

    F -->|MAC Address| T[Enter MAC Address<br/>Username & Password]
    T --> U[Click Next]
    U --> V[Select Device Node]

    V --> W{Node Type}

    %% ONVIF
    W -->|ONVIF Node| X[Find Device]
    X --> Y[Search Network<br/>Resolve Network Address]
    Y --> Z[Authenticate Device<br/>Validate ONVIF]
    Z --> AA{Validation Successful?}

    AA -->|No| AB[Display Error<br/>Retry]
    AB --> T

    AA -->|Yes| O

    %% CI
    W -->|CI Node| AC[Find Device]
    AC --> AD[Search Network<br/>Resolve Network Address]
    AD --> AE[Send Configuration]
    AE --> AF[Device Connects to CI Node]
    AF --> AG{Connection Successful?}

    AG -->|No| AH[Display Error<br/>Retry]
    AH --> T

    AG -->|Yes| O

%% ----------------------------
%% Common Flow
%% ----------------------------

    O --> AI[Review Summary]
    AI --> AJ[Click Add Device]
    AJ --> AK[Register Device]
    AK --> AL[Associate Device with Selected Node]
    AL --> AM([Device Added Successfully])
