---
title: get_sortExpressions()
page_title: get_sortExpressions() | UI for ASP.NET AJAX Documentation
description: get_sortExpressions()
slug: grid/client-side-programming/gridtableview-object/collections/get_sortexpressions()
tags: get_sortexpressions()
published: True
position: 1
---

# get_sortExpressions()



## 

A collection of __Telerik.Web.UI.GridSortExpression__ objects. Represents the sort expressions applied for the grid instance. The __toString()__ javascript method executed over this collection will return coma separated string of all expressions (in case of AllowMultiColumnSorting) or a single sort expression if multi-column sorting is disabled. You can also utilize the __toList()__ javascript method in order to pass an array of items (representing the sort expressions applied) to the server and operate with them using a GridSortExpression server-side object. Each sort expression (of type __Telerik.Web.UI.GridSortExpression__) has *fieldName* and *sortOrder* properties which hold the *DataField* of the sorted column and the sort direction (Ascending, Descending or None). To retrieve the values from these properties use the __get_fieldName()__ and __get_sortOrder()__ properties of the corresponding GridSortExpression.

Below is a sample code excerpt using OnCommand client event handler:

````ASPNET
	    <telerik:RadGrid ID="RadGrid1" runat="server">
	        <ClientSettings>
	            <clientEvents OnCommand="RaiseCommand" />
	        </ClientSettings>
	    </telerik:RadGrid>
````



````JavaScript
	        function RaiseCommand(sender, args) {
	            args.set_cancel(true); //cancel the default command to prevent postback/ajax request
	
	            var sortExpressions = sender.get_masterTableView().get_sortExpressions();
	
	            //obtain the values from the GridSortExpression properties
	            if (sortExpressions.length > 0) {
	                var expression = sortExpressions._array[0];
	                var fieldName = expression.get_fieldName();
	                var sortOrder = expression.get_sortOrder();
	            }
	
	            alert(sortExpressions.toString());
	        }
	
````



>note The RadGrid get_sortExpressions() property is meaningful only in case the RadGrid control is bound client-side.
>
