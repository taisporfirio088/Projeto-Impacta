@startuml

' Tabelas principais com campos
entity "Colaboradores" as Colaboradores {
  *ID : int <<PK>>
  Idade : int
  Média Desempenho geral empresa : float
  Média Engajamento geral empresa : float
  Modelo de Trabalho : string
  Nacionalidade : string
  Nível de Experiência : string
  Nome : string
  Plano de Saúde Adicional (Filhos) : bool
  Qtd Filhos : int
  Salário Mensal : float
  Tempo de Serviço : int
  Tipo de Contrato : string
  Vale Alimentação : float
  Vale Transporte : float
}

entity "Contratacoes" {
  Admissoes : int
  Ano : int <<FK>>
  Demissoes (Com Justa Causa) : int
  Demissoes (Sem Justa Causa) : int
  Funcionarios Colaboradores Acumulados : int
  Mês : string
  Admissoes Hierarquia : string
}

entity "Historico_Contratacoes" {
  Admissoes : int
  Ano : int <<FK>>
  Mês : string
  Demissoes (Justa Causa) : int
  Demissoes (Sem Justa Causa) : int
  Funcionarios Acumulados : int
  Ano Hierarquia : string
}

entity "Treinamentos" {
  ID do Treinamento : int <<PK>>
  Data do Treinamento : date
  Duração (dias) : int
  Nome do Treinamento : string
  Quantidade de Vagas : int
  Tipo de Treinamento : string
}

entity "Despesas" {
  Categoria : string
  Valor (R$) : float
}

entity "Vendas" {
  Custo Desenvolvimento : float
  Data Assinatura : date
  Data Entrega : date
  Lucro Previsto Cliente : float
  Lucro Previsto Empresa : float
  Nome Empresa : string
  País Cliente : string
  Satisfação Cliente : float
  Segmento Cliente : string
  Status Projeto : string
  Tipo Software : string
}

entity "Faturamento" {
  Ano : int <<PK>>
  Faturamento Total : float
  Lucro Total Empresa : float
  Quantidade de Contratos : int
  Ticket Médio : float
}

' Relacionamentos
Colaboradores -- Treinamentos : "ID → Treinamentos"
Contratacoes -- Faturamento : "Ano"
Contratacoes -- Historico_Contratacoes : "Ano"
Colaboradores -- Contratacoes : "ID → FK implícita"
@enduml
