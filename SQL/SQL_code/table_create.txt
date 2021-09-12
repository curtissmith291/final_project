-- Create Beer Table
CREATE TABLE beer_info (
	beer_id INT PRIMARY KEY,
	beer_Name VARCHAR,
	beer_Style VARCHAR,
	Style_Key INT,
	Brewery VARCHAR,
	Description TEXT,
	ABV DECIMAL,
	Ave_Rating DECIMAL,
	Min_IBU DECIMAL,
	Max_IBU DECIMAL,
	Astringency DECIMAL,
	Body DECIMAL,
	Alcohol DECIMAL,
	Bitter DECIMAL,
	Sweet DECIMAL,
	Sour DECIMAL,
	Salty DECIMAL,
	Fruits DECIMAL,
	Hoppy DECIMAL,
	Spices DECIMAL,
	Malty DECIMAL
	);
	
SELECT * FROM beer_info
LIMIT 10;