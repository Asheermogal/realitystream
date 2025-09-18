# RealityStream Development Notes

## Overview
RealityStream is a machine learning pipeline for processing and analyzing various datasets including bees, blinks, and industrial data. This document contains important development notes and troubleshooting information.

## Common Issues & Solutions

### CSV Loading Issues
- **BOM (Byte Order Mark) Problems**: CSV files may contain UTF-8 BOM characters that can cause parsing issues. Always strip BOM using `csvText.replace(/^\uFEFF/, '')` after fetching.
- **Caching Issues**: During development, browsers may cache CSV files. Use `fetch(url, { cache: 'no-store' })` to prevent caching issues.

### Parameter Management
- **Hash vs Query Parameters**: Script loading parameters (`showheader`, `showsearch`) should be query parameters, not hash parameters.
- **Custom YAML URLs**: When using custom parameter files, ensure proper encoding/decoding of URLs in hash parameters.

### Development Workflow
1. Always test with fresh browser cache when modifying CSV or YAML files
2. Use browser dev tools to monitor network requests for caching issues
3. Validate CSV files for BOM characters before deployment
4. Test parameter loading with various combinations of hash and localStorage states

## File Structure
- `/parameters/` - Parameter configuration files
- `/input/` - Input datasets organized by type (bees, blinks, industries, trees)
- `/output/` - Model outputs and results
- `/models/` - Model implementations and templates
- `/process/` - Data processing scripts and notebooks

## Key Components
- **Parameter Loading**: Handles CSV-based parameter file selection
- **YAML Processing**: Parses and merges YAML configurations with hash parameters
- **Model Pipeline**: Processes data through various ML models
- **Output Generation**: Creates reports and visualizations

## Debugging Tips
- Check browser console for parameter loading errors
- Verify CSV file encoding and format
- Test with different parameter combinations
- Monitor network tab for caching issues
- Validate YAML syntax before loading
