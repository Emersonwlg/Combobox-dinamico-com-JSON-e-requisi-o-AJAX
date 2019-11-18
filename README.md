# Combobox dinâmico com JSON e requisição AJAX
## No código descreve como popular um combobox dinâmico usando requisição ajax.  


    $selectCliente.on('change', function () {
        $.ajax({
            url: '/Atendimento/BuscarDadosBancariosCliente',
            type: 'GET',
            data: {
                codCliente: $selectCliente.val()
            },
            success: function (data) {
                    $codigoBanco.val(data.CodigoBanco);
                     $agenciaBanco.val(data.AgenciaBanco);
                    $contaBanco.val(data.ContaBanco);
                    $descricaoBanco.val(data.DescricaoBanco);
            }
        });
    });
    
    
    # Controller
    
    public JsonResult BuscarDadosBancariosCliente(int codCliente)  
    {
        var resultado = PreencherDadosBancarios(codCliente);
        return Json(resultado, JsonRequestBehavior.AllowGet);
    }

