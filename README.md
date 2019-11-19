# Combobox dinâmico com JSON e requisição AJAX
*No trecho de código abaixo é descrito como popular um combobox, através de uma requisição ajax no qual é chamado o método da Controller (C#).*


#### JavaScript  

 ```javascript
    (function () {
    
        var $selectCliente = $('#IdCliente');
                   
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
    })();
