---
layout: post
title: Bulk edit Active Directory user attributes (Powershell)
---

<code></code><code>PowerShell
&lt;#Get list of current O365 users:
$ODusers = (get-aduser -filter * -Properties Name, SamAccountName, extensionAttribute15 | where {$_.extensionAttribute15 -eq "attribute"} | select-object Name, SamAccountName)
$ODUsers | sort-object SamAccountName | Out-Gridview

#Audit specific users:
'user1','user2' | % {get-aduser $_ -Properties Name, SamAccountName, extensionAttribute15 | select-object Name, SamAccountName, extensionAttribute15 | ft Name, SamAccountName, extensionAttribute15 -auto}

#Enable specific users:
$ext = "attribute"
$users = ('user1','user2')
$users | % {set-aduser $_ -clear "extensionAttribute15"; set-aduser $_ -add @{extensionAttribute15=$ext}}
</code><code></code>

<code></code><code>PowerShell
&lt;#
.Synopsis
   Short description
.DESCRIPTION
   Long description
.EXAMPLE
   Example of how to use this cmdlet
.EXAMPLE
   Another example of how to use this cmdlet
#&gt;
function Verb-Noun
{
    [CmdletBinding()]
 
    [OutputType([int])]
 
    Param
    (
        # Param1 help description
        [Parameter(Mandatory=$true,
                   ValueFromPipelineByPropertyName=$true,
                   Position=0)]
        $Param1,
 
        # Param2 help description
        [int]
        $Param2
    )
 
    Begin
    {
    }
 
    Process
    {
    }
 
    End
    {
    }
}
</code><code></code>
