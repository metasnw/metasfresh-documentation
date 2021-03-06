---
title: IT FRESH-455

required data:
   * bpartner: bpartner G000X (customer) for OrgX and G000Y (also customer) for OrgY
   * products: P000X from OrgX, P000Y from OrgY
   * Organizations: OrgX, OrgY 
  * E-Mail Server Routing : 
    * Mail_Combination_Base_X : DocBaseType "Material Delivery", DocSubType Empty, Organization OrgX
    * Mail_Combination_SubType_X : DocBaseType "Material Delivery", DocSubType "Produktauslieferung", Organization OrgX
        * To only be created after testing with Mail_Combination_Base_X
    * Mail_Combination_Base_Y : DocBaseType "Material Delivery", DocSubType Empty, Organization OrgY
    * Mail_Combination_SubType_Y : DocBaseType "Material Delivery", DocSubType "Produktauslieferung", Organization OrgY
        * To only be created after testing with Mail_Combination_Base_Y
  * layout: default
---

### different email per org in inout print preview
> Testcase to check if the email in Shipment print preview fits the organization of the shipment

**Org e-mail in InOut Print Preview**

1. Correct email in Shipment of OrgX for Material Delivery DocBaseType
    * Log in with OrgX
    * Make sure the partner G000X does not have a printing format set/active (this can be verified in the Partner window, Print Format tab)
    * Make sure you have Mail_Combination_Base_X but not Mail_Combination_SubType_X
    * Create a Sales Order for organization OrgX, partner G000X
	* Go to the created Shipment Schedule
	* Create a Shipment out of it, complete it
	* Go to the created Shipment, press on Print Preview 
		* => OK: The email in the report is the email from Mail_Combination_Base_X

2. Correct email in Shipment of OrgX for Material Delivery DocBaseType, "Produktauslieferung" DocSubType
    * Log in with OrgX
    * Make sure the partner G000X does not have a printing format set/active (this can be verified in the Partner window, Print Format tab)
    * Make sure you have Mail_Combination_Base_X and Mail_Combination_SubType_X
    * Create a Sales Order for organization OrgX, partner G000X
	* Go to the created Shipment Schedule
	* Create a Shipment out of it, complete it
	* Go to the created Shipment, press on Print Preview 
		* => OK: The email in the report is the email from Mail_Combination_SubType_X
		
3. Correct email in Shipment of OrgY for Material Delivery DocBaseType
    * Log in with OrgY
    * Make sure the partner G000Y does not have a printing format set/active (this can be verified in the Partner window, Print Format tab)
    * Make sure you have Mail_Combination_Base_Y but not Mail_Combination_SubType_Y
    * Create a Sales Order for organization OrgY, partner G000Y
	* Go to the created Shipment Schedule
	* Create a Shipment out of it, complete it
	* Go to the created Shipment, press on Print Preview 
		* => OK: The email in the report is the email from Mail_Combination_Base_Y

4. Correct email in Shipment of OrgY for Material Delivery DocBaseType, "Produktauslieferung" DocSubType
    * Log in with OrgY
    * Make sure the partner G000Y does not have a printing format set/active (this can be verified in the Partner window, Print Format tab)
    * Make sure you have Mail_Combination_Base_Y and Mail_Combination_SubType_Y
    * Create a Sales Order for organization OrgY, partner G000Y
	* Go to the created Shipment Schedule
	* Create a Shipment out of it, complete it
	* Go to the created Shipment, press on Print Preview 
		* => OK: The email in the report is the email from Mail_Combination_SubType_Y
		

3. Regression
    * Go to an old Shipment of OrgX, for a partner who has no printing format set
    * Print Preview
        * => OK: The email is the default email of OrgX
    * Repeat the same steps for OrgY
        * => OK: THe email is the default email of OrgY
