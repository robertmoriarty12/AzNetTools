
#################################################################################################
#The variables in this block are the only variables that will change based on the user's goals and resource names.



$portRangeMax = 25  ##Creates DNAT Rules for ports 1-25.  If you want to predefine port numbers, don't use this block and start at line 16.
$portList = 1,2
for($i = 2; $i -lt $portRangeMax; $i++){
    $portList+= ($i+1)

}



$portList = 3389, 445, 443, 80, 22, 5, 2 #Ports for external inbound translation | If the port range method above is selected, do not run this line
$translatedAddress = "10.0.3.3" #Customer's VMs
$fwVIP = "13.89.139.166"
$fwName = "testScriptFW"
$ResourceGroupName = "romoriarTesting"
$azFw = Get-AzFirewall -Name $fwName -ResourceGroupName $ResourceGroupName

#The above $ variables are the only things that need to change 
#################################################################################################



#PS Limitation: Two entries required to initialize a PS array.  Therefore, first two indices of the array with be manually created.
#The subsequential indices will start at 2 and will be entered via loop.

#creates a string array for rule names    
$ruleNameList = "rule0", "rule1"  

for($j = 2; $j -lt $portList.length; $j++){
    $ruleNameList+= ("rule_"+ $j.toString())
}


#creates a ruleObjectArray 
$rule1 = New-AzFirewallNatRule -Name $ruleNameList[0] -Protocol "UDP","TCP" -SourceAddress "*" -DestinationAddress $fwVIP -DestinationPort $portList[0] -TranslatedAddress $translatedAddress -TranslatedPort $portList[0]
$rule2 = New-AzFirewallNatRule -Name $ruleNameList[1] -Protocol "UDP","TCP" -SourceAddress "*" -DestinationAddress $fwVIP -DestinationPort $portList[1] -TranslatedAddress $translatedAddress -TranslatedPort $portList[1] 
$ruleObjectList = $rule1, $rule2

$ruleCollection = New-AzFirewallNatRuleCollection -Name "MyNatRuleCollectionTest" -Priority 100 -Rule $rule1
$ruleCollection.AddRule($rule2)

    

#creates a DNAT rule for each port supplied by the customer.
for($i = 2; $i -lt $portList.length; $i++){
    

   $ruleObjectList += New-AzFirewallNatRule -Name $ruleNameList[$i] -Protocol "UDP","TCP" -SourceAddress "*" -DestinationAddress $fwVIP -DestinationPort $portList[$i] -TranslatedAddress $translatedAddress -TranslatedPort $portList[$i] 
   $ruleCollection.AddRule($ruleObjectList[$i])
   Write-Output $i
}

$azFw.NatRuleCollections = $ruleCollection
Set-AzFirewall -AzureFirewall $azFw
