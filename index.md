---
layout: post
---

<html lang="en">
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<meta http-equiv="x-ua-compatible" content="ie=edge">
		<meta name="description" content="Improve entity framework performance with Bulk SaveChanges, Bulk Insert, update, delete and merge using your dbcontext. C# Entity Framework Library.">
		<meta name="keywords" content="EntityFramework BulkSaveChanges BulkInsert BulkUpdate BulkDelete BulkMerge Insert Update Delete Merge SQLServer SQLAzure SQLCompact MySQL SQLite">
		<meta name="msvalidate.01" content="89359D9C492A475C0061398008D105FB" />
		<title>EntityFramework Bulk Insert, update, delete and merge in SQL Server, SQL Azure, SQL Compact, MySQL and SQLite</title>
		<link rel="icon" type="image/png" href="http://entityframework-extensions.net/images/logo.png">
		<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.2/css/bootstrap.min.css" integrity="sha384-y3tfxAZXuh4HwSYylfB+J125MxIs6mR5FOHamPBG064zB+AFeWH94NdvaCBm8qnd" crossorigin="anonymous">
		<link rel="stylesheet" type="text/css" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css">
		<link rel="stylesheet" type="text/css" href="http://entityframework-extensions.net/css/github.css">
	</head>
	
	<body>
  
		<!-- anchor !-->
		<a id="download" href="#"></a>
		<a id="github" href="#"></a>
		
		<!-- top-header !-->
		<div id="top-header">
			<div class="container">
				<div class="text-right">
					<a href="mailto:info@zzzprojects.com"><i class="fa fa-envelope"></i>&nbsp;&nbsp;info@zzzprojects.com</a>
					<a href="https://www.facebook.com/zzzprojects" target="_blank"><i class="fa fa-facebook"></i></a>
					<a href="https://twitter.com/zzzprojects" target="_blank"><i class="fa fa-twitter"></i></a>
					<a href="https://plus.google.com/+Zzzprojects_NetSQL/posts" target="_blank"><i class="fa fa-google-plus"></i></a>
					<a href="http://zzzprojects.us9.list-manage.com/subscribe?u=cecbc4775cf67bf1ff82018af&id=4765ffa5f8" target="_blank" class="hidden-sm-down"><i class="fa fa-newspaper-o"></i></a>
				</div>
			</div>
		</div>
		
		<!-- header !-->
		<header>
			<div class="container">
				<div class="row">
					<div class="col-lg-6">
						<div class="card">
							<div class="card-block">
								<h1 class="card-title">C# Bulk Operations</h1>
								<h3>Solve Entity Framework performance issue when saving with high performance bulk operations and hundred of flexibles feature.</h3>
								<hr class="m-y-md" />
								<div class="lead">
									<a href="https://www.nuget.org/packages/Z.EntityFramework.Extensions/" target="_blank" class="btn btn-success btn-lg btn-left" role="button"><span><i class="fa fa-cloud-download fa-2x"></i>&nbsp;<span>Download</span></span></a>
									<a href="https://github.com/zzzprojects/EntityFramework-Extensions" target="_blank" class="btn btn-primary btn-lg btn-right" role="button"><span><i class="fa fa-github fa-2x"></i>&nbsp;<span>GitHub</span></span></a>				
								</div>
							</div>
						</div>
					</div>
					<div class="col-lg-1">
					</div>
					<div class="col-lg-6">
						<div class="card">
							<div class="card-block card-code">
{% highlight csharp %}
var context = new CustomerContext();
// ... context code ...

// Easy to use
context.BulkSaveChanges();

// Easy to customize
context.BulkSaveChanges(operation => operation.BatchSize = 1000);

// Perform specific bulk operations
context.BulkDelete(customers);
context.BulkInsert(customers);
context.BulkUpdate(customers);

// Customize Primary Key
context.BulkMerge(customers, operation => {
   operation.ColumnPrimaryKeyExpression = customer => customer.Code;
});
{% endhighlight %}	
							</div>
						</div>
					</div>
				</div>
			</div>
		</header>
		
		<!-- anchor !-->
		<a id="features" href="#"></a>
		
		<!-- features !-->
		<div id="feature">
			<div class="container">
			
				<!-- Scalable !-->
				<h2>Scalable</h2>
				<p>SQL Server - Benchmarks</p>
				<table class="table table-striped table-hover" style="background-color: white;">
					<tr class="thead-inverse">
						<th>Operations</th>
						<th>100 Rows</th>
						<th>1,000 Rows</th>
						<th>10,000 Rows</th>
					</tr>
					<tr>
						<th>BulkSaveChanges</th>
						<td>20 ms</td>
						<td>200 ms</td>
						<td>2,000 ms</td>
					</tr>
					<tr>
						<th>Insert</th>
						<td>2 ms</td>
						<td>6 ms</td>
						<td>25 ms</td>
					</tr>
					<tr>
						<th>Update</th>
						<td>27 ms</td>
						<td>50 ms</td>
						<td>80 ms</td>
					</tr>
					<tr>
						<th>Delete</th>
						<td>25 ms</td>
						<td>45 ms</td>
						<td>70 ms</td>
					</tr>
					<tr>
						<th>Merge</th>
						<td>30 ms</td>
						<td>65 ms</td>
						<td>160 ms</td>
					</tr>
				</table>
				<p class="font-italic">As fast as SqlBulkCopy for insert but with way more capabilities</p>

				<!-- Extensible !-->
				<h2>Extensible</h2>
				<p>Support Multiple SQL Providers:</p>
				<ul>
					<li>SQL Server 2008+</li>
					<li>SQL Azure</li>
					<li>SQL Compact</li>
					<li>MySQL</li>
					<li>SQLite</li>
				</ul>
				
				<!-- BulkSaveChanges !-->
				<h2>Insert - Output Identity Value</h2>
				<h3>Problem</h3>
				<p>You need to save hundreds or thousands of entities but you are not satisfied with Entity Framework performance.</p>
				<h3>Solution</h3>
				<p>BulkSaveChanges is exactly like SaveChanges but perform way faster. It’s easy to use, you only need to replace “SaveChanges” by “BulkSaveChanges” and you are done!</p>
{% highlight csharp %}
// Upgrade SaveChanges performance with BulkSaveChanges
var context = new CustomerContext();
// ... context code ...

// Easy to use
context.BulkSaveChanges();

// Easy to customize
context.BulkSaveChanges(operation => operation.BatchSize = 1000);
{% endhighlight %}	
				<h3>Scalability</h3>
				<p>BulkSaveChanges is as fast as SaveChanges with one entity and quickly become 10-50x faster with hundreds and thousands of entities.</p>
				
				<!-- Bulk Operations !-->
				<h2>Bulk Operations</h2>
				<h3>Problem</h3>
				<p>You need even more performance then BulkSaveChanges, save detached entities or save entities in a specific order.</p>
				<h3>Solution</h3>
				<p>Use bulk operations such as bulk insert, update, delete and merge which perform operation on specified entities and bypass the change tracker to increase performance.</p>
{% highlight csharp %}
// Perform specific bulk operations on entities
context.BulkDelete(customers);
context.BulkInsert(customers);
context.BulkUpdate(customers);
context.BulkMerge(customers);
{% endhighlight %}	
				<h3>Maintainability</h3>
				<p>Bulk Operation use directly the Entity Framework Model. Even if you change column name or change inheritance (TPC, TPH, TPT), Bulk operation will continue to work as expected.</p>
				
				<!-- Custom Key !-->
				<h2>Custom Key</h2>
				<h3>Problem</h3>
				<p>You need to perform an update, delete or merge using a specific custom key like the custom code.</p>
				<h3>Solution</h3>
				<p>Specify your own key by customizing the operation.</p>
{% highlight csharp %}
// Use flexible features such as specifying the primary key
context.BulkMerge(customers, operation => {
   operation.ColumnPrimaryKeyExpression = customer => customer.Code;
});
{% endhighlight %}	
				<h3>Flexibility</h3>
				<p>Bulk operations offers hundred of customization such as BatchSize, Custom Key, Custom Mapping, etc.</p>
			</div>
		</div>
		
		<!-- anchor !-->
		<a id="pro" href="#"></a>
		
		<!-- pricing !-->
		<div id="pricing">
			<div class="container">
				<div class="row">
					<div class="col-lg-6">
						<h2>Pricing</h2>
						<hr class="m-y-md" />
						<ul>
							<li>Make your application work faster</li>
							<li>Make your customer do their job better</li>
							<li>Make your customer happier!</li>
						</ul>
						<hr class="m-y-md" />
						<p>Every month, a <a href="https://www.nuget.org/packages/Z.EntityFramework.Extensions/" target="_blank">FREE trial</a> of the PRO version is available to let you evaluate all its features without limitations.</p>					
					</div>
					<div class="col-lg-6">
						<table class="table table-hover table-bordered">
							<thead class="thead-inverse">
								<tr>
									<th></th>
									<th>PRO</th>
								</tr>
							</thead>
							<tbody>
								<tr>
									<th>Bulk SaveChanges</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
								<tr>
									<th>Bulk Insert</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
								<tr>
									<th>Bulk Update</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
								<tr>
									<th>Bulk Delete</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
								<tr>
									<th>Bulk Merge</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
								<tr>
									<th>DeleteFromQuery</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
								<tr>
									<th>UpdateFromQuery</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
								<tr>
									<th>Commercial License</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
								<tr>
									<th>Royalty-Free</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
								<tr>
									<th>Support & Upgrades (1 year)</th>
									<td><i class="fa fa-check-square-o fa-2x"></i></td>
								</tr>
							</tbody>
						</table>
						
						<form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top" onsubmit="return purchase_validate()">
							<input type="hidden" name="cmd" value="_s-xclick">
							<input type="hidden" name="currency_code" value="USD">
							<fieldset class="form-group">
								<input type="hidden" name="on0" value="Seats">
								<select id="provider_type" name="hosted_button_id" class="form-control" onchange="selectProduct()">
									<option value="GS977QXB98R2C">SQL Server/ Azure Provider</option>
									<option value="5WVPWVNDGRHH6">SQL Compact Provider</option>
									<option value="55WDUT7ENJBKU">SQLite Provider</option>
									<option value="32JM43GUXW4ZW">MySQL Provider</option>
									<option value="TSCGQDC4YR2MQ">ALL Providers</option>
								</select> 
								<br />
								<select id="single_product" name="os0" class="form-control">
									<option value="1 seat">Bulk Operations $599 (1 seat)</option>
									<option value="2-4 seats" selected>Bulk Operations $799 (2-4 seats)</option>
									<option value="5-9 seats">Bulk Operations $999 (5-9 seats)</option>
									<option value="10-14 seats">Bulk Operations $1199 (10-14 seats)</option>
									<option value="15-19 seats">Bulk Operations $1399 (15-19 seats)</option>
								</select> 
								<select id="bundle_product" name="os0" class="form-control">
									<option value="1 seat">Bulk Operations $799 (1 seat)</option>
									<option value="2-4 seats" selected>Bulk Operations $999 (2-4 seats)</option>
									<option value="5-9 seats">Bulk Operations $1199 (5-9 seats)</option>
									<option value="10-14 seats">Bulk Operations $1399 (10-14 seats)</option>
									<option value="15-19 seats">Bulk Operations $1599 (15-19 seats)</option>
								</select> 
							</fieldset>
							<div class="checkbox">
								<label>
									<input id="agree_agreement" type="checkbox">I have read and agree to the <a href="http://www.zzzprojects.com/license-agreement/" target="_blank">License Agreement</a>.
								</label>
							</div>
							<button type="submit" class="btn btn-success btn-lg"><span><i class="fa fa-shopping-cart"></i>&nbsp;<span>BUY NOW</span></span></button>
							<br />
							<div>* Contact us for invoice or payment method alternative.</div>
						</form>					
					</div>
				</div>
			</div>
			
			<!-- validation !-->
			<div id="error_validation" class="modal fade" tabindex="-1" role="dialog" aria-labelledby="modal_agreement" aria-hidden="true">
				<div class="modal-dialog" role="document">
					<div class="modal-content">
						<div class="modal-header">
							<h4 class="modal-title" id="modal_agreement">License Agreement</h4>
						</div>
						<div class="modal-body bg-danger">
							You must read and agree to the License Agreement.
						</div>
						<div class="modal-footer">
							<button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
						</div>
					</div>
				</div>
			</div>
		</div>
		
		<!-- support !-->
		<div id="support">
			<div class="container">
				<h2>Test our Outstanding Support</h2>
				<h3>We usually answer within the next business day, hour, or minutes!</h3>
				<div class="row">
					<hr class="hidden-sm-up" />
					<div class="col-sm-6 col-lg-3">
						<div class="card">
							<div class="card-block">
								<h4 class="card-title">Documentation</h4>
							</div>
							<a href="https://github.com/zzzprojects/EntityFramework-Extensions/wiki" target="_blank"><i class="fa fa-folder-open fa-5x"></i></a>
							<div class="card-block">
								<p class="card-text">Consult our complete documentation to help you getting started.</p>
								<a href="https://github.com/zzzprojects/EntityFramework-Extensions/wiki" target="_blank">Documentation</a>
							</div>
						</div>
					</div>
					<hr class="hidden-sm-up" />
					<div class="col-sm-6 col-lg-3">
						<div class="card">
							<div class="card-block">
								<h4 class="card-title">Contact Us</h4>
							</div>
							<a href="mailto:info@zzzprojects.com"><i class="fa fa-users fa-5x"></i></a>
							<div class="card-block">
								<p class="card-text">Email our team for any type of questions. We love to hear from you!</p>
								<a href="mailto:info@zzzprojects.com">info@zzzprojects.com</a>
							</div>
						</div>
					</div>
					<hr class="hidden-sm-up" />
					<div class="col-sm-6 col-lg-3">
						<div class="card">
							<div class="card-block">
								<h4 class="card-title">Forum</h4>
							</div>
							<a href="https://github.com/zzzprojects/EntityFramework-Extensions/issues" target="_blank"><i class="fa fa-weixin fa-5x"></i></a>
							<div class="card-block">
								<p class="card-text">Visit the forum to propose new features or to discuss about the library.</p>
								<a href="https://github.com/zzzprojects/EntityFramework-Extensions/issues" target="_blank">Forum</a>
							</div>
						</div>
					</div>
					<hr class="hidden-sm-up" />
					<div class="col-sm-6 col-lg-3">
						<div class="card">
							<div class="card-block">
								<h4 class="card-title">Open Source</h4>
							</div>
							<a href="https://github.com/zzzprojects/EntityFramework-Extensions" target="_blank"><i class="fa fa-github fa-5x"></i></a>
							<div class="card-block">
								<p class="card-text">Access the partial source of the library you're using. (Under development)</p>
								<a href="https://github.com/zzzprojects/EntityFramework-Extensions" target="_blank">GitHub</a>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>

		<!-- other product !-->
		<div id="product">
			<div class="container">
				<div class="row">
					<div class="col-lg-3">
						<h3>Entity Framework</h3>
						<ul>
							<li><a href="http://www.zzzprojects.com/products/dotnet-development/entity-framework-extensions/" target="_blank">Entity Framework Extensions</a></li>
							<li><a href="https://github.com/zzzprojects/EntityFramework-Plus" target="_blank">Entity Framework Plus (EF+)</a></li>
						</ul>
					</div>
					<div class="col-lg-3">
						<h3>Bulk Operations</h3>
						<ul>
							<li><a href="http://www.zzzprojects.com/products/dotnet-development/entity-framework-extensions/" target="_blank">.NET Entity Framework Extensions</a></li>
							<li><a href="http://www.zzzprojects.com/products/dotnet-development/bulk-operations/" target="_blank">.NET Bulk Operations</a></li>
						</ul>
					</div>
					<div class="col-lg-3">
						<h3>Expression Evaluator</h3>
						<ul>
							<li><a href="http://eval-sql.net/" target="_blank">Eval SQL.NET</a></li>
							<li><a href="http://eval-expression.net/" target="_blank">Eval Expression.NET</a></li>
						</ul>
					</div>
					<div class="col-lg-3">
						<h3>Others</h3>
						<ul>
							<li><a href="http://www.zzzprojects.com/products/dotnet-development/extension-methods/" target="_blank">Extension Methods</a></li>
							<li><a href="https://github.com/zzzprojects/LINQ-Async" target="_blank">LINQ Async</a></li>
						</ul>
					</div>
				</div>
			</div>		
		</div>
		
		<!-- footer !-->
		<footer>
			<div class="container text-center-md-down">
				<div class="row">
					<div class="col-lg-6">
						Copyright © <a href="http://www.zzzprojects.com/" target="_blank" class="text-bold">ZZZ Projects Inc.</a> 2014 - 2016
						<div class="hidden-lg-up"></div>
						All rights reserved
					</div>
					<hr class="hidden-lg-up" />
					<div class="col-lg-6 text-right-lg-up social">
						<a href="https://www.facebook.com/zzzprojects" target="_blank"><i class="fa fa-facebook"></i></a>
						<a href="https://twitter.com/zzzprojects" target="_blank"><i class="fa fa-twitter"></i></a>
						<a href="https://plus.google.com/+Zzzprojects_NetSQL/posts" target="_blank"><i class="fa fa-google-plus"></i></a>
						<a href="http://zzzprojects.us9.list-manage.com/subscribe?u=cecbc4775cf67bf1ff82018af&id=4765ffa5f8" target="_blank"><i class="fa fa-newspaper-o"></i></a>
					</div>
				</div>
			</div>
		</footer>

	<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.4/jquery.min.js"></script>
	<script src="js/tether.min.js"></script>
	<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.2/js/bootstrap.min.js" integrity="sha384-vZ2WRJMwsjRMW/8U7i6PWi6AlO1L79snBrmgiDpgIWJ82z8eA5lenwvxbMV1PAh7" crossorigin="anonymous"></script>
	<script type="text/javascript">
	  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
	  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
	  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
	  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

	  ga('create', 'UA-55584370-8', 'auto');
	  ga('send', 'pageview');
	  
	  function purchase_validate() {
		if($("#agree_agreement").prop('checked')) {
			return true;
		}
		
		$("#error_validation").modal('show')
		return false;
	  }
	  
	  $("#bundle_product").hide();
	  function selectProduct() {
		if($("#provider_type").val() == "TSCGQDC4YR2MQ") {
			$("#single_product").hide();
			$("#bundle_product").show();
		}
		else {
			$("#single_product").show();
			$("#bundle_product").hide();
		}
	  }
	</script>
	</body>
</html>

<style>
/* general */
* {
	 font-family: "Bitter",Georgia,"Times New Roman",serif;
}
.highlight * {
	font-family: Consolas, "Liberation Mono", Menlo, Courier, monospace;
}
.text-bold {
	font-weight: 700;
}
.text-green {
	color: rgb(68, 157, 68);
}
@media (max-width: 61em) {
	.text-center-md-down {
		text-align: center;
	}
}
@media (max-width: 33em) {
	.text-center-xs-down {
		text-align: center;
	}
}
@media (min-width: 62em) {
	.text-right-lg-up {
		text-align: right;
	}
}

/* section general */
#top-header {
	background-color: #111;
	border-bottom: 1px solid #000;
	font-size: 14px;
	padding: 5px 0px;
}
header {
	background: -moz-linear-gradient(top, #222, #333);
    background: -webkit-linear-gradient(top, #222, #333);
    background: -ms-linear-gradient(top, #222, #333);
    background: -o-linear-gradient(top, #222, #333);
    background: linear-gradient(top, #222, #333);
	border-bottom: 1px solid #111;
	border-top: 1px solid #333;
	padding: 40px 0px;
}
#announcement {
	background-color: #c00;
	color: #f1f1f1;
	font-weight: 700;
	font-style: italic;
	padding: 5px; 0px;
}
#feature {
    background: -moz-linear-gradient(top, #ddd, #f2f2f2);
    background: -webkit-linear-gradient(top, #ddd, #f2f2f2);
    background: -ms-linear-gradient(top, #ddd, #f2f2f2);
    background: -o-linear-gradient(top, #ddd, #f2f2f2);
    background: linear-gradient(top, #ddd, #f2f2f2);
	border-bottom: 1px solid #ddd;
    border-top: 1px solid #eee;
	padding-bottom: 60px;
}
#pricing {
	background-color: #fefefe;
	padding-top: 60px;
	padding-bottom: 60px;
}
#support {
	background: -moz-linear-gradient(top, #eee, #bbb);
    background: -webkit-linear-gradient(top, #eee, #bbb);
    background: -ms-linear-gradient(top, #eee, #bbb);
    background: -o-linear-gradient(top, #eee, #bbb);
    background: linear-gradient(top, #eee, #bbb);
	padding-top: 60px;
	padding-bottom: 60px;
	border-bottom: 1px solid #aaa;
	border-top: 1px solid #ccc;
}
#product {
    background: -moz-linear-gradient(top, #111, #222);
    background: -webkit-linear-gradient(top, #111, #222);
    background: -ms-linear-gradient(top, #111, #222);
    background: -o-linear-gradient(top, #111, #222);
    background: linear-gradient(top, #111, #222);
	border-bottom: 1px solid #111;
	border-top: 1px solid #333;
	color: #fefefe;
	padding: 20px 0px;
}
footer {
	background: -moz-linear-gradient(top, #333, #222);
    background: -webkit-linear-gradient(top, #333, #222);
    background: -ms-linear-gradient(top, #333, #222);
    background: -o-linear-gradient(top, #333, #222);
    background: linear-gradient(top, #333, #222);
	border-top: 1px solid #444;
	color: #666;
	padding-top: 5px;
	padding-bottom: 5px;
}

/* top-header */
#top-header a {
	color: #fefefe;
	padding-left: 10px;
	padding-right: 10px;
	text-decoration: none;
} 
#top-header a:hover {
	opacity: 0.7;
    transition: all 0.4s ease-in-out 0s;
}

/* header */
header .card {
	background-color: transparent;
	border: none;
	color: #f1f1f1;
}
header .card h1 {
	font-size: 3.0rem;
}
header .card h3 {
	font-size: 1.3rem;
}
header .card hr {
	border-color: initial;
}
header .card .lead .btn {
	width: 175px;
}
header .card .lead .btn-left {
	margin-right: 20px;
}
header .card .lead .btn span {
	display: inline-block;
	height: 40px;
}
header .card .lead .btn span span {
	vertical-align : middle;
}
header .card .lead .text-muted {
	font-size: 14px;
	padding-top: 10px;
}
header .card .card-code {
	background-color: #f1f1f1;
	border: 2px solid #444;
	color: #000;
	min-height: 350px;
}
header .card .card-code {
	padding: 0px;
}
header .card .card-code .highlight,
header .card .card-code .highlight pre {
	background-color: transparent;
	border: none;
}
header .card .card-contents {
	font-size: 18px;
}

header .card .card-contents a {
	color: #f1f1f1;
}

header .card .card-contents a:hover {
	opacity: 0.7;
	text-decoration: none;
    transition: all 0.4s ease-in-out 0s;
}

@media (max-width: 33em) {
	header .card h1 {
		font-size: 2.5rem;
	}
	header .card .lead .btn {
		margin-bottom: 20px;
	}
}

/* feature */
#feature h2 {
	border-bottom: 2px solid #000;
	font-size: 32px;
	letter-spacing: 2px;
	padding-top: 30px;
	padding-bottom: 10px;
}
#feature h3 {
	letter-spacing: 1px;
	font-size: 16px;
	font-weight: 700;
	padding-top: 10px;
}
#feature .btn {
	margin-top: 40px;
}
@media (min-width: 62em) {
	#feature .row .col-lg-6:first-child {
		padding-right: 45px;
	}
	#feature .row .col-lg-6:last-child {
		padding-left: 45px;
	}
}

/* pricing */
#pricing h2 {
	margin-bottom: -10px;
}
#pricing .table thead th {
	text-align: center;
}
#pricing .table td {
	text-align: center;
}
#pricing .fa-times {
	color: #c9302c;
}
#pricing .fa-check-square-o {
	color: #449D44;
}

/* support */
#support {
	text-align: center;
}
#support h2 {
	padding-bottom: 20px;
}
#support h3 {
	font-size: 20px;
	padding-bottom: 40px;
}
#support .card {
	border: 0.0625rem solid #ccc;
}
#support .card-text {
	min-height: 75px;
}
#support i {
	color: #0275d8;
}

/* product */
#product h3 {
	letter-spacing: 1px;
	font-size: 18px;
	font-weight: 700;
}
#product ul {
	list-style: none;
	padding-left: 0px;
}
#product ul li {
	padding-top: 5px;
}
#product a {
	color: #999;
	font-size: 14px;
	letter-spacing: 0.5px;
}
#product a:hover {
	color: #fefefe;
	opacity: 0.9;
	text-decoration: none;
    transition: all 0.4s ease-in-out 0s;
}

/* footer */
@media (max-width: 61em) {
  footer {
	padding: 20px 0;
  }
}
footer hr {
	border-color: #666;
	margin: 20px;
}
footer a {
	color: #666;
}
footer a:hover {
	color: #666;
	opacity: 0.7;
	text-decoration: none;
    transition: all 0.4s ease-in-out 0s;
}
footer .social a {
	font-size: 24px;
	padding: 0px 10px;
}
</style>