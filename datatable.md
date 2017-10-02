1.	进入datatable所在界面时,尚未对其进行搜索操作,未传参至后台,因此`if params.key?("ck_id")`为`false`;

2.	当前datatable为模态框,点击某行触发后缀为.js的action为上一界面赋值,此时应确保当前界面含有

	`<script>
	  $(".asset-link").attr("data-remote","true");
	</script>`

	全文为
    
	`<%= datatable_view({:count => @count, :datas => @datas}) do |builder| %>`
	    
        &emsp;`<% builder.column(:event_code, {:title => "申请单号"}) do |a| %>`
		
        &emsp;&emsp;`<a href="/events/set_event_for_sale?id=<%= a[:id] %>" class="asset-link"><%= a[:event_code] %></a>`
	  
      &emsp;`<% end %>`

		&emsp;`<% builder.column(:created_by, {:title => t(:label_asset_created_by)}) do |a| %>`
		
        &emsp;&emsp;`<%= Irm::Person.find_by_id(a[:created_by]).full_name %>`
	    
        &emsp;`<% end %>`
	    
        &emsp;`<% builder.column(:created_at, {:title => t(:label_asset_created_at)}) %>`
	
    `<% end %>`
	
    `<script>`
	  
      &emsp;`$(".asset-link").attr("data-remote","true");`
	
    `</script>`

