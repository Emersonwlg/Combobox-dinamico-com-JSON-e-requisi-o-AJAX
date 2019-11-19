# Combobox dinâmico com JSON e requisição AJAX
*No trecho de código abaixo é descrito como popular um combobox, através de uma requisição ajax no qual é chamado o método da Controller (C#).*

### JavaScript  

 
functio(
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
    

    #### Controller  
    
    #region [PROPERTIES]
    
    private readonly IAtendimentoService _atendimentoService;
    
    #endregion
    
    #region [CONSTRUCTOR]
    
     public AtendimentoController(IAtendimentoService atendimentoService)
     {
        _atendimentoService = atendimentoService;
     }
    
    #endregion
      
    #region [ACTIONS]
    
    public JsonResult BuscarDadosBancariosCliente(int codCliente)  
    {
        var resultado = PreencherDadosBancarios(codCliente);
        return Json(resultado, JsonRequestBehavior.AllowGet);
    }
    
    #endregion
    
    #region [METHODS]
    
    private CadastroPagamentoClienteViewModel PreencherDadosBancarios(int codCliente)
    {
        var model = new CadastroPagamentoClienteViewModel();
        var resultado = _atendimentoService.BuscarDadosBancariosCliente(codCliente);

        if (resultado != null)
        {
            model = new CadastroPagamentoClienteViewModel()
            {
                CodigoBanco = resultado.NumBanco,
                AgenciaBanco = resultado.AgenciaBanco,
                ContaBanco = resultado.ContaBanco,                    
                DescricaoBanco = resultado.NomeBanco
            };
        }
        return model;
    }
        
    #endregion
