# Honeypot-Detector

This Python script is designed to analyze a cryptocurrency token (a "memecoin") and determine if it exhibits characteristics of a honeypot. 
Honeypot: A type of scam where users can buy but not sell the token. It does so by fetching data from the Dexscreener API, checking trading patterns, and applying various risk factors.

Steps involved in writing this script:

Here’s a structured numeric breakdown of the code:

1. Importing Dependencies
  requests (for API calls)
  datetime (for time calculations)
2. Fetching Token Data
  Function: get_memecoin_info(contract_address)
  Sends API request to Dexscreener
  Returns JSON data or None if request fails
3. Calculating Risk Percentage
  Function: calculate_risk_percentage(risk_factors)
  Computes total risk weight
  Ensures risk percentage does not exceed 100%
4. Honeypot Detection Logic
  4.1 Extracting Key Trading Data
    Retrieves trading pairs
    Fetches buy/sell transactions for 24h, 6h, 1h
    Extracts liquidity, market cap, price change
    Converts pair creation timestamp
  4.2 Defining Risk Thresholds
    Buy/Sell ratio thresholds
    Liquidity and market cap thresholds
    Recent token creation thresholds
  4.3 Applying Risk Factors
    Assigns weights based on suspicious activity
    Flags new pairs, high buy/sell ratios, low liquidity, missing information
  4.4 Final Risk Calculation
    Calls calculate_risk_percentage(risk_factors)
    If risk exists, returns an alert & risk percentage
    Otherwise, returns safe token status
5. Finally Running the Script
  Accepts contract address input
  Calls get_memecoin_info() to fetch data
  Runs is_honeypot() for risk analysis
  Prints honeypot warning or safe token message
