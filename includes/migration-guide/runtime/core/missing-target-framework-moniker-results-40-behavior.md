### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Ausência do Moniker da Estrutura de Destino resulta no comportamento da versão 4.0

|   |   |
|---|---|
|Detalhes|Os aplicativos sem um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> aplicado no nível de assembly serão executados automaticamente usando a semântica (quirks) do .NET Framework 4.0. Para garantir a alta qualidade, é recomendável que todos os binários sejam explicitamente atribuídos com um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> indicando a versão do .NET Framework com a qual eles foram criados. Usar um moniker da estrutura de destino em um arquivo de projeto fará com que o MSBuild aplique automaticamente um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>.|
|Sugestão|O <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> deve ser fornecido, seja por meio da adição do atributo diretamente ao assembly ou da especificação de uma estrutura de destino no [arquivo de projeto, seja por meio da GUI das propriedades do projeto do Visual Studio](https://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio- managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx).|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Tempo de execução|

