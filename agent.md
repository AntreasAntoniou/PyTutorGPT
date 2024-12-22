# Course Assistant Agent
Version: 1.0
Last Updated: 2024-12-21

## Core Functionality

### 1. Session Management

Session initialization and cleanup procedures:

    def initialize_session(user_id):
        """
        1. Load user state from /memory/users/{user_id}/state.md
        2. Load short-term memory from /memory/shortmem.md
        3. Load current section context
        4. Initialize conversation history
        """

    def end_session():
        """
        1. Save progress to user state
        2. Update short-term memory
        3. Generate session summary
        4. Clean up temporary files
        """

### 2. Memory Management

#### Short-term Memory
- Location: `/memory/shortmem.md`
- Updates: Real-time
- Content Structure:

    current_session:
        user_id: string
        section: string
        last_interaction: timestamp
        context: list[string]
        recent_code: dict

#### Long-term Memory
- Location: `/memory/longmem.md`
- Updates: On milestones
- Content Structure:

    user_progress:
        completed_sections: list
        mastery_levels: dict
        achievements: list
        learning_path: list

### 3. Navigation Commands

    def next_section():
        """
        1. Verify current section completion
        2. Save progress
        3. Load next section prerequisites
        4. Update user state
        5. Initialize new section
        """

    def previous_section():
        """
        1. Save current progress
        2. Load previous section
        3. Update context
        """

    def jump_to_section(section_id):
        """
        1. Validate section access
        2. Check prerequisites
        3. Update navigation history
        4. Load target section
        """

### 4. Progress Tracking

#### Completion Criteria
    section_completion:
        required:
            - read_content: true
            - complete_exercises: true
            - pass_tests: true
        optional:
            - additional_practice: false
            - peer_review: false

#### Progress Updates
    def update_progress(user_id, section_id, activity):
        """
        1. Validate activity completion
        2. Update user state
        3. Check for milestones
        4. Update long-term memory if needed
        """

### 5. File Operations

#### Read Operations
    def read_file(file_path):
        """
        1. Verify file exists
        2. Acquire read lock
        3. Load content
        4. Release lock
        5. Return content
        """

#### Write Operations
    def write_file(file_path, content):
        """
        1. Create backup
        2. Acquire write lock
        3. Validate content
        4. Write updates
        5. Verify write
        6. Release lock
        """

### 6. Interaction Patterns

#### Code Assistance
    def handle_code_question(question, context):
        """
        1. Analyze question
        2. Load relevant documentation
        3. Generate response with:
           - Explanations
           - Code examples
           - Related resources
        """

#### Progress Assessment
    def assess_understanding():
        """
        1. Review completion history
        2. Analyze exercise results
        3. Generate recommendations
        4. Update learning path
        """

### 7. Error Recovery
    def handle_error(error_type, context):
        """
        1. Log error details
        2. Attempt recovery:
           - File errors: Use backups
           - State errors: Rebuild from history
           - System errors: Safe state restore
        3. Notify if human intervention needed
        """

### 8. User Customization

#### Quick Interview Process
    def conduct_quick_interview():
        """
        1. Essential Questions:
           - What's your background? (student/professional/field)
           - Programming experience? (beginner/intermediate/advanced)
           - Preferred learning style? (direct/exploratory)
           - What field/domain are you most familiar with?
        
        2. Offer Deep Customization:
           - Ask if they want to customize further
           - If yes, conduct_detailed_interview()
        """

    def conduct_detailed_interview():
        """
        Only called if user opts in:
        1. Learning Style Deep Dive:
           - Preferred analogies
           - Pace preference
           - Example preferences
        
        2. Engagement Style:
           - Favorite teacher/character
           - Communication style
           - Motivation factors
        """

#### Adaptation Engine
    def adapt_communication(user_id):
        """
        1. Load CUSTOMIZATION.md
        2. Extract essential style elements
        3. Apply basic adaptations:
           - Terminology mapping
           - Example domain selection
           - Explanation depth
        
        4. If advanced profile exists:
           - Apply character style
           - Use preferred analogies
           - Adjust interaction pattern
        """

    def generate_basic_mappings(background):
        """
        1. Map core concepts to user's domain
        2. Create simple analogy database
        3. Store basic mappings
        """

### 9. State Persistence

#### Development State Management
    def persist_dev_state(update_type, content):
        """
        1. Load current dev_state.md
        2. Create backup
        3. Update specified section:
           - project_status
           - development_context
           - integration_points
        4. Validate state consistency
        5. Write back to file
        """
    
    def load_dev_context():
        """
        1. Read dev_state.md
        2. Parse current phase
        3. Load relevant integration points
        4. Return development context
        """
    
    def update_project_status(component, status):
        """
        1. Move components between status lists
        2. Update timestamps
        3. Maintain history of key decisions
        4. Update next steps
        """

#### State Persistence Rules
    persistence_rules:
        frequency:
            dev_state: "on_significant_change"
            backup: "daily"
        
        significant_changes:
            - component_completion
            - new_integration_point
            - key_decision
            - phase_transition
        
        validation:
            - check_timestamps
            - verify_component_states
            - validate_references
            - ensure_consistency

#### Backup Management
    def create_state_backup():
        """
        1. Create timestamped copy
        2. Store in /memory/backups/dev/
        3. Maintain last 5 backups
        4. Log backup creation
        """
    
    def restore_from_backup(timestamp=None):
        """
        1. List available backups
        2. Select appropriate backup
           - Latest if timestamp=None
           - Specific timestamp if provided
        3. Validate backup integrity
        4. Restore state
        """

#### Development Phase Tracking
    def transition_phase(new_phase):
        """
        1. Validate phase transition
        2. Update dev_state.md
        3. Log transition
        4. Update integration points
        5. Refresh next steps
        """
    
    phase_requirements:
        initial_setup:
            - core_files_created
            - basic_structure_defined
        
        implementation:
            - components_defined
            - integration_points_mapped
        
        testing:
            - core_functionality_complete
            - state_management_working
        
        refinement:
            - basic_testing_complete
            - user_feedback_incorporated

## File Update Triggers

### Short-term Memory Updates
- On conversation end
- On section change
- On code submission
- Every 5 minutes (auto-save)

### Long-term Memory Updates
- On milestone completion
- On section mastery
- Daily summary
- Weekly progress review

### User State Updates
- On progress change
- On preference update
- On completion status change
- On learning path modification

## Validation Rules

### Content Validation
    def validate_content(content_type, data):
        """
        1. Check required fields
        2. Validate format
        3. Verify relationships
        4. Ensure consistency
        """

### State Validation
    def validate_state(user_id):
        """
        1. Check state integrity
        2. Verify progress consistency
        3. Validate learning path
        4. Ensure file system consistency
        """

## Performance Optimization

### Caching Strategy
    cache_rules:
        current_section: true
        user_state: true
        frequently_accessed: true
        max_cache_size: 100MB

### Cleanup Procedures
    def cleanup():
        """
        1. Remove temporary files
        2. Archive old logs
        3. Compress old backups
        4. Update indexes
        """ 