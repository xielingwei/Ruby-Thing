`<%= link_to("删除", {:action => "delete_approve_person", :id => data[:id]}, data: {confirm: "确认删除该审批人?"}, :method => :delete, :class => "action-link delete-person") %>`

`data: {confirm: "xxx"}`
点击按钮弹出, 仅有[OK]及[取消]按钮;
