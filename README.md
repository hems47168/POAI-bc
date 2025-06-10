# POAI-bc
class Rule:
    def __init__(self, premise, conclusion):
        self.premise = premise
        self.conclusion = conclusion

class KnowledgeBase:
    def __init__(self):
        self.rules = []
        self.facts = set()

   def add_rule(self, rule):
        self.rules.append(rule)

   def add_fact(self, fact):
        self.facts.add(fact)

   def query(self, query):
        return self.backward_chaining(query, set())

   def backward_chaining(self, query, visited):
        if query in self.facts:
            return True
        if query in visited:
            return False
        visited.add(query)
        for rule in self.rules:
            if rule.conclusion == query:
                if
                self.evaluate_premise(rule.premise, visited):
                    return True
        return False

  def evaluate_premise(self, premise, visited):
        if premise in self.facts:
            return True
        for rule in self.rules:
            if rule.conclusion == premise:
        if self.evaluate_premise(rule.premise, visited):
                    return True
        return self.backward_chaining(premise, visited)

# Create knowledge base
knowledge_base = KnowledgeBase()

# Add rules
knowledge_base.add_rule(Rule("A", "B"))
knowledge_base.add_rule(Rule("C", "D"))
knowledge_base.add_rule(Rule("B and D", "E"))

# Add facts
knowledge_base.add_fact("A")
knowledge_base.add_fact("C")

# Query knowledge base
print(knowledge_base.query("E"))  # True
print(knowledge_base.query("F"))  # False

# Modify rules and facts for 'and' condition handling
class Rule:
    def __init__(self, premise, conclusion):
        self.premise = premise
        self.conclusion = conclusion

class KnowledgeBase:
    def __init__(self):
        self.rules = []
        self.facts = set()

   def add_rule(self, rule):
        self.rules.append(rule)

   def add_fact(self, fact):
        self.facts.add(fact)

   def query(self, query):
        return self.backward_chaining(query, set())

   def backward_chaining(self, query, visited):
        if query in self.facts:
            return True
        if query in visited:
            return False
        visited.add(query)
        for rule in self.rules:
            if rule.conclusion == query:
                premises = rule.premise.split(' and ')
                if all(self.backward_chaining(premise, visited) for premise in premises):
                    return True
        return False

# Create knowledge base
knowledge_base = KnowledgeBase()

# Add rules
knowledge_base.add_rule(Rule("A and C", "E"))
knowledge_base.add_rule(Rule("F", "G"))

# Add facts
knowledge_base.add_fact("A")
knowledge_base.add_fact("C")

# Query knowledge base
print(knowledge_base.query("E"))  # True
print(knowledge_base.query("G"))  # False
