# Combobox dinâmico com JSON e requisição AJAX

## JavaScript 

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
    
