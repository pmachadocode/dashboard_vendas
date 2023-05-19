# Dashboard vendas

![image](https://github.com/pmachadocode/dashboard_vendas/assets/49794067/416f38b9-2dce-4434-8e98-fbb3a4bd8476)


Medidas Ultilizadas - Modelo de dados

Total_Venda_C_Desc:=sum(Vendas[Total_Venda])
Qtd_Produtos_Vendidos:=sum(Vendas[Qtd_Vendida])
Total_Desconto:=sum(Vendas[Valor do desconto])

Qtd_Vendas:=DISTINCTCOUNT(Vendas[ID_Venda])

Ticket_Medio_Venda_Liq:=DIVIDE([Total_Venda_C_Desc];[Qtd_Vendas];BLANK())
%_Vendas_Online:=DIVIDE([Total_Vendas_Online];[Total_Venda_C_Desc];BLANK())
%_Venda_Proprios:=DIVIDE([Total_Vendas_Contoso];[Total_Venda_C_Desconto];BLANK())

Total_Venda_S_Desc:=sumx(Vendas;Vendas[Preço unitário]*[Qtd_Vendida])

Vendas_C_Desc_2011:=CALCULATE([Qtd_Vendas];FILTER('Calendar';'Calendar'[Year]=2011))
Vendas_C_Desc_2012:=CALCULATE([Qtd_Vendas];FILTER('Calendar';'Calendar'[Year]=2012))
Vendas_C_Desc_2013:=CALCULATE([Qtd_Vendas];FILTER('Calendar';'Calendar'[Year]=2013))
Total_Vendas_Loja:=CALCULATE([Total_Venda_C_Desc];FILTER(Vendas;[Id_Canal]=1))
Total_Vendas_Online:=CALCULATE([Total_Venda_C_Desc];FILTER(Vendas;[Id_Canal]=2))
Total_Vendas_Catalogo:=CALCULATE([Total_Venda_C_Desconto];FILTER(Vendas;[Id_Canal]=3))
Total_Vendas_Revenda:=CALCULATE([Total_Venda_C_Desconto];FILTER(Vendas;[Id_Canal]=4))
Total_Vendas_Contoso:=CALCULATE([Total_Venda_C_Desconto];FILTER(Produtos;Produtos[Fabricante]="Contoso, Ltd"))
 
Total_Venda_YoY:=CALCULATE([Total_Venda_C_Desconto];DATEADD('Calendar'[Date];-1;YEAR))
Ticket_Medio_YoY:=CALCULATE([Ticket_Medio_Venda_Liq];DATEADD('Calendar'[Date];-1;YEAR))
