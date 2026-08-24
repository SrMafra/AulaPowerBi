Calendario = 
VAR _MinData = MIN ( vendas[DataVenda] )
VAR _MaxData = MAX ( vendas[DataVenda] )
RETURN
ADDCOLUMNS (
    CALENDAR ( _MinData, _MaxData ),
    "Ano", YEAR ( [Date] ),
    "NumeroMes", MONTH ( [Date] ),
    "NomeMes", FORMAT ( [Date], "MMMM" ),
    "NomeMesAbrev", FORMAT ( [Date], "MMM" ),
    "MesAno", FORMAT ( [Date], "MMM/AAAA" ),
    "Trimestre", "T" & QUARTER ( [Date] ),
    "AnoTrimestre", YEAR ( [Date] ) & "-T" & QUARTER ( [Date] ),
    "Dia", DAY ( [Date] ),
    "DiaSemanaNum", WEEKDAY ( [Date], 2 ),
    "NomeDiaSemana", FORMAT ( [Date], "dddd" ),
    "Semana", WEEKNUM ( [Date], 2 ),
    "FimDeSemana", IF ( WEEKDAY ( [Date], 2 ) > 5, "Sim", "Não" ),
    "AnoMes", YEAR ( [Date] ) * 100 + MONTH ( [Date] )
)


----------------------------

Total Vendas = SUM ( vendas[ValorTotal] )

_-______-_______

Vendas Ano Anterior = 
CALCULATE (
    [Total Vendas],
    SAMEPERIODLASTYEAR ( Calendario[Date] )
)




