flowchart TD

    A([Start])
    A --> B[Open Device Manager]
    B --> C[Click Add Device]

    C --> D{Addition Method}

%%=========================================================
%% MANUAL ADDITION
%%=========================================================

    D -->|Manual| M1[Select Camera]

    M1 --> M2{Identification Method}

%%------------- Network Address -----------------

    M2 -->|Network Address| M3[Enter Network Address<br/>IPv4 / IPv6 / Hostname<br/>Port, Protocol, Credentials]
    M3 --> M4[Select Device Node]

    M4 --> M5{Node Type}

    M5 -->|ONVIF| M6[Test Connection]
    M6 --> M7[Validate Reachability<br/>Authentication<br/>ONVIF Compatibility]
    M7 --> M8{Success?}

    M8 -->|No| M9[Display Error & Retry]
    M9 --> M3

    M8 -->|Yes| MR[Review Summary]

    M5 -->|CI| M10[Send Configuration]
    M10 --> M11[Camera Connects to CI Node]
    M11 --> M12{Success?}

    M12 -->|No| M13[Display Error & Retry]
    M13 --> M3

    M12 -->|Yes| MR

%%------------- MAC Address -----------------

    M2 -->|MAC Address| M20[Enter MAC Address<br/>Credentials]
    M20 --> M21[Select Device Node]

    M21 --> M22{Node Type}

    M22 -->|ONVIF| M23[Find Device]
    M23 --> M24[Resolve Network Address]
    M24 --> M25[Authenticate & Validate ONVIF]
    M25 --> M26{Success?}

    M26 -->|No| M27[Display Error & Retry]
    M27 --> M20

    M26 -->|Yes| MR

    M22 -->|CI| M28[Find Device]
    M28 --> M29[Resolve Network Address]
    M29 --> M30[Send Configuration]
    M30 --> M31[Camera Connects to CI Node]
    M31 --> M32{Success?}

    M32 -->|No| M33[Display Error & Retry]
    M33 --> M20

    M32 -->|Yes| MR

%%------------- Manual Completion -----------------

    MR --> M40[Click Add Device]
    M40 --> Z

%%=========================================================
%% AUTO DISCOVERY
%%=========================================================

    D -->|Auto Discovery| A1[Select Discovery Scope]

    A1 --> A2{Scope}

    A2 -->|All Nodes| A5[Use All Configured Nodes]

    A2 -->|Specific Node| A3[Select Node]
    A3 --> A4[Optional Custom IP Range]

    A4 --> A5

    A5 --> A6[Click Search]

    A6 --> A7[Run ONVIF Discovery]
    A6 --> A8[Run UPnP Discovery]

    A7 --> A9
    A8 --> A9

    A9[Merge Discovery Results]

    A9 --> A10[Remove Duplicate Cameras]

    A10 --> A11[Retain Discovery Node Information]

    A11 --> A12[Display Discovered Cameras]

    A12 --> A13[Select One or More Cameras]

    A13 --> A14{Node Assignment}

    A14 -->|Use Discovery Node| A15[Assign Camera to Discovery Node]

    A14 -->|Assign Fixed Node| A16[Select Fixed Node]

    A15 --> A17{Integration Type}
    A16 --> A17

%%------------- ONVIF -----------------

    A17 -->|ONVIF Node| A18[Enter Username & Password]

    A18 --> A19[Authenticate Cameras]

    A19 --> A20[Validate ONVIF Compatibility]

    A20 --> A21{Success?}

    A21 -->|No| A22[Report Failed Cameras]

    A21 -->|Yes| Z

%%------------- CI -----------------

    A17 -->|CI Node| A23[Send Integration Configuration]

    A23 --> A24[Camera Applies Configuration]

    A24 --> A25[Camera Connects to CI Node]

    A25 --> A26{Success?}

    A26 -->|No| A27[Report Failed Cameras]

    A26 -->|Yes| Z

%%=========================================================
%% COMMON END
%%=========================================================

    Z[Register Device(s)]
    Z --> Z1[Associate with Selected Node(s)]
    Z1 --> Z2[Add to Platform Inventory]
    Z2 --> Z3([Available for Monitoring, Recording, Analytics & Events])
