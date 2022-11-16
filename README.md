- 👋 Hi, I’m @Ad7492
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Ad7492/Ad7492 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
anychart.onDocumentReady(function () {

// The data used in this sample can be obtained from the CDN

// https://cdn.anychart.com/csv-data/csco-daily.js

// create data table on loaded data

var dataTable = anychart.data.table();

dataTable.addData(get_csco_daily_data());

// map loaded data

var mapping = dataTable.mapAs();

mapping.addField("open", 1, "first");

mapping.addField("high", 2, "max");

mapping.addField("low", 3, "min");

mapping.addField("close", 4, "last");

mapping.addField("value", 5, "value");

// create stock chart

var chart = anychart.stock();

// create plot on the chart

var plot = chart.plot(0);

// create line series

var ohlcSeries = plot.ohlc(mapping);

ohlcSeries.name("CSCO");

ohlcSeries.stroke("2px #64b5f6");

// create KDJ indicator

var kdj = plot.kdj(mapping, 10, "EMA", 10, "SMA", 20);

kdj.kSeries().stroke("#bf360c");

kdj.dSeries().stroke("#02660c");

kdj.jSeries().stroke("#0228b2");

// set container id for the chart

chart.container("container");

// initiate chart drawing

chart.draw();

});
