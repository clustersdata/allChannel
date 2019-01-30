# allChannel
allChannel
<%- include('components/header') %>
	<%- include('components/hint') %>
	<%- include('components/nav') %>
	<div class="container">
		
		<div id="page-content">
			<div id="all-channel-information" class="table-responsive">
				<table class="table table-hover">

					<form class="form-inline" role="form">
						<h3 class="all-channel-title">全部订阅号</h3>
			            <div id="nav-search" class="form-group">
			                <label class="sr-only" for="name">名称</label> 
			                <input type="text" class="form-control" id="name" placeholder="search...">
			            </div>
			            <i class="glyphicon glyphicon-search"></i>
		            </form>
					
				<thead>
				  <tr id='tableHeader' class="table-head">
				  	<th>Index</th>
				    <th>订阅号名称</th>
				    <th>订阅号量</th>
				    <th>订阅号Id</th>
				    <th>订阅号Youtube地址</th>
				  </tr>
				</thead>

				
				<% allChannelList.forEach(function(channel){ %>
				
				<tbody>
				  <tr>
				    <td> <%= skip+1 %> </td>
				    <td class="channel-name"> <a href="/channel/<%= channel.channelId %>"><%= channel.channel %> </a></td>
				    <td> <%= channel.subscriber %> </td>
				    <td> <%= channel.channelId %> </td>
				    <td> <a href="<%= channel.channelUrl %>" target=_blank><%= channel.channelUrl %></a> </td>
				  </tr>
				  
				</tbody>
				<% skip++ %>
				<% }) %>

				</table>
				</div>
		</div>
		
		<!-- pagnation -->
		<nav>
		  <ul class="pager">
		    <% if(page!==1){ %>
		      <li class="previous"><a href="/channel?page=<%= page-1 %>">&larr; 上一页</a></li>
		    <% }else{ %>
		      <li class="previous"></li>
		    <% } %>
		    
		    <li>共<%= pages %>页 第<%= page %>页</li>
		    <% if(page!==pages){ %>
		      <li class="next"><a href="/channel?page=<%= page+1 %>">下一页 &rarr;</a></li>
		    <% }else{ %>
		      <li class="next"></li>
		    <% } %>
		  </ul>
		</nav>	
	</div>
    
<%- include('components/footer') %>
