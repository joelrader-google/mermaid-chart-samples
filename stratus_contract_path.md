```mermaid
gitGraph
   %% OPP represents the 'main' branch
   commit id: "Workload Analysis"
   commit id: "Approved Quote"
   
   %% Handoff to USDA
   branch USDA
   checkout USDA
   commit id: "Review & Add Fee"
   
   %% Handoff to Customer
   branch Gov_Customer
   checkout Gov_Customer
   commit id: "Submit IAA" type: HIGHLIGHT 
   
   commit id: "or IAA Mod" tag:"2025.10.01"
   %%% Add a URL to next steps after IAA go/next-steps-here
   
   %% Return to USDA
   checkout USDA
   merge Gov_Customer id: "IAA Received"
   commit id: "Submit BAR"
   commit id: "Issue ATP/MOD"
   %% BAR = Basic Allocation of Resources
   %% Order Management Product Fulfillment

   %% ATP Received, Continue with OMPF
   branch OMPF
   checkout OMPF
   commit id: "Continue with OMPF"
   
   %% Return to OPP
   checkout main
   merge USDA id: "Contract Award"
   commit id: "Open Case/Order"
   
   %% Handoff to OMPF
   %%branch OMPF
   checkout OMPF
   commit id: "Provision PSSA"
   %% Operational
   
   %% Final Handoff to Customer
   checkout Gov_Customer
   merge OMPF id: "Ready for Use"
   commit id: "Migrate & Invoice"

%% Hyperlinks
```
